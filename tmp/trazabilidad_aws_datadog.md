# Guía Técnica: Trazabilidad Cruzada entre AWS CloudWatch y Datadog APM

## 🎯 Objetivo de la Arquitectura
El objetivo de esta guía es establecer una estrategia de correlación bidireccional entre los identificadores de trazabilidad generados nativamente por la infraestructura de **AWS** (como API Gateway, ALB, AppSync) y los propios generados por el agente de **Datadog** (DD APM) en un servicio basado en **Java Spring Boot**. Esto nos permitirá un seguimiento de punta a punta (End-To-End).

## 🔍 Estrategia Principal: Correlación Bidireccional

Existen dos flujos asimétricos que debemos conectar:
1. **De Datadog hacia CloudWatch:** Inyectar el `dd.trace_id` de Datadog en los logs recolectados por AWS CloudWatch.
2. **De AWS hacia Datadog:** Capturar el origen de las peticiones que entrega AWS (`X-Amzn-Trace-Id`) e inyectarlos en tu APM de Datadog.

A continuación vemos el detalle de ambas implementaciones.

---

## FASE 1: De Datadog hacia CloudWatch (Inyección en Logs MDC)

El agente de Datadog (javaagent) puede agregar automáticamente los IDs de correlación dentro del log de tu aplicación (vía Mapped Diagnostic Context o MDC).

### 1.1 Configuración de Variables de Entorno
Debes arrancar tu aplicación Java asegurándote de contar con las siguientes variables (ya sea en ECS, EKS, EC2, o local):

```bash
DD_LOGS_INJECTION=true
DD_SERVICE=mi-microservicio
DD_ENV=produccion
```
*`DD_LOGS_INJECTION=true` autoriza a Datadog a poblar tu MDC.*

### 1.2 Configuración del `logback-spring.xml`
Una vez que el MDC es poblado por Datadog, debes exponer estos atributos (`dd.trace_id`, `dd.span_id`) dentro del formato de log enviado a la salida estándar o a los appenders configurados para CloudWatch Logs.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <!-- Incluimos los defaults de Spring Boot -->
    <include resource="org/springframework/boot/logging/logback/defaults.xml"/>
    <include resource="org/springframework/boot/logging/logback/console-appender.xml" />
    
    <!-- Appender JSON / Texto estructurado para Cloudwatch (Ejemplo texto plano incluyendo MDC) -->
    <appender name="CONSOLE_WITH_DATADOG" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <!-- Aquí el patrón inyecta el dd.trace_id, dd.span_id y el aws.trace_id manualmente -->
            <pattern>%d{yyyy-MM-dd HH:mm:ss} [%thread] %-5level %logger{36} - [dd.trace_id=%X{dd.trace_id:-} dd.span_id=%X{dd.span_id:-} aws.trace_id=%X{aws.trace_id:-}] %msg%n</pattern>
        </encoder>
    </appender>

    <!-- Usar JSON es una mejor práctica para CloudWatch Logs porque facilita querys en Insights -->
    <!-- Requiere dependencia logstash-logback-encoder -->
    <!--
    <appender name="JSON_AWSCW" class="ch.qos.logback.core.ConsoleAppender">
        <encoder class="net.logstash.logback.encoder.LogstashEncoder">
            <includeMdcKeyName>dd.trace_id</includeMdcKeyName>
            <includeMdcKeyName>dd.span_id</includeMdcKeyName>
            <includeMdcKeyName>aws.trace_id</includeMdcKeyName>
        </encoder>
    </appender>
    -->

    <root level="INFO">
        <appender-ref ref="CONSOLE_WITH_DATADOG" />
    </root>
</configuration>
```

---

## FASE 2: De AWS hacia Datadog (Autocaptura de Headers de AWS)

AWS introduce un header en todas las solicitudes que pasan por un ALB o un API Gateway llamado `X-Amzn-Trace-Id`. Necesitamos inyectar este Header al Root Trace de Datadog APM.

### 2.1 Configuración del Agente / Variables de Entorno
Indícale al Tracer de Datadog que todo header que llegue con este nombre, sea agregado automáticamente como tag de infraestructura dentro de APM.

```bash
DD_TRACE_HEADER_TAGS="X-Amzn-Trace-Id:aws.trace_id"
```
*Acá estamos mapeando el header HTTP `X-Amzn-Trace-Id` al Tag interno de Datadog llamado `aws.trace_id`.*

### 2.2 Filtro Interceptor en Java (Opcional pero Recomendado para Log de App Local)
Para estar doblemente seguros de que el trace ID también queda en tus Custom Logs a disposición de la lógica de negocio (por si el Agente por alguna razón no lo enlaza instantáneamente al Root Context MDC de la Request HTTP), procedemos a configurar este filtro manual simple.

Crea esta clase en tu paquete `config` o `filters` de Spring Boot:

```java
package com.tuempresa.proyecto.config;

import org.slf4j.MDC;
import org.springframework.stereotype.Component;

import jakarta.servlet.Filter;
import jakarta.servlet.FilterChain;
import jakarta.servlet.ServletException;
import jakarta.servlet.ServletRequest;
import jakarta.servlet.ServletResponse;
import jakarta.servlet.http.HttpServletRequest;
import java.io.IOException;

@Component
public class AwsTraceIdFilter implements Filter {

    // El Header generado por el Ingress (ALB / API Gateway)
    private static final String AWS_TRACE_ID_HEADER = "X-Amzn-Trace-Id";
    
    // Key a almacenar en Logback / MDC
    private static final String AWS_TRACE_ID_MDC_KEY = "aws.trace_id";

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) 
            throws IOException, ServletException {
            
        if (request instanceof HttpServletRequest) {
            HttpServletRequest req = (HttpServletRequest) request;
            String awsTraceId = req.getHeader(AWS_TRACE_ID_HEADER);
            
            if (awsTraceId != null && !awsTraceId.trim().isEmpty()) {
                MDC.put(AWS_TRACE_ID_MDC_KEY, awsTraceId);
            }
        }
        
        try {
            chain.doFilter(request, response);
        } finally {
            // Limpiar MDC para reutilizar el thread pool correctamente (muy importante en Tomcat/Undertow)
            MDC.remove(AWS_TRACE_ID_MDC_KEY);
        }
    }
}
```

---

## FASE 3: Despliegue en AWS ECS (Fargate o EC2)

Al ejecutar la aplicación en contenedores de ECS, la forma en que los logs viajan hacia CloudWatch y cómo el Agente de Datadog reside junto a la aplicación requiere consideraciones especiales.

Existen dos estrategias principales para desplegar el **Datadog Agent** en ECS:
1. **ECS con instancias EC2 (Daemon Service):** El agente de Datadog corre como un servicio daemon (una instancia por cada nodo EC2). Todos los contenedores de Spring Boot envían sus trazas allí.
2. **ECS Fargate (Patrón Sidecar):** Al ser "serverless", cada tarea (*Task Definition*) de Fargate no comparte un sistema operativo host con otras. Por lo tanto, el contenedor de Datadog debe declararse como un contenedor *Sidecar* junto al contenedor de tu app Java dentro de la misma definición.

### 3.1 Configuración de Task Definition en ECS Fargate (JSON)

Para que todo funcione, este JSON de ejemplo muestra la configuración de ambos contenedores y cómo se envían los logs de la app de Spring Boot directo a CloudWatch a través del controlador `awslogs`.

```json
{
  "family": "spring-boot-fargate-task",
  "networkMode": "awsvpc",
  "containerDefinitions": [
    {
      "name": "spring-boot-app",
      "image": "tu-registro-aws.dkr.ecr.region.amazonaws.com/mi-app:latest",
      "essential": true,
      "environment": [
        { "name": "DD_ENV", "value": "produccion" },
        { "name": "DD_SERVICE", "value": "mi-app-backend" },
        { "name": "DD_LOGS_INJECTION", "value": "true" },
        { "name": "DD_TRACE_HEADER_TAGS", "value": "X-Amzn-Trace-Id:aws.trace_id" },
        { "name": "DD_AGENT_HOST", "value": "127.0.0.1" }
      ],
      "logConfiguration": {
        "logDriver": "awslogs",
        "options": {
          "awslogs-group": "/ecs/mi-app-backend-logs",
          "awslogs-region": "us-east-1",
          "awslogs-stream-prefix": "java"
        }
      }
    },
    {
      "name": "datadog-agent",
      "image": "public.ecr.aws/datadog/agent:latest",
      "essential": true,
      "environment": [
        { "name": "DD_API_KEY", "value": "TU_API_KEY_AQUI" },
        { "name": "DD_SITE", "value": "datadoghq.com" },
        { "name": "DD_APM_ENABLED", "value": "true" },
        { "name": "DD_APM_NON_LOCAL_TRAFFIC", "value": "true" }
      ]
    }
  ],
  "requiresCompatibilities": ["FARGATE"],
  "cpu": "1024",
  "memory": "2048"
}
```
*💡 **Mecanismo:** Dado que ambos contenedores comparten la misma red interna de la Task, tu contenedor Java envía las trazas mediante APM al Agente Sidecar de Datadog sencillamente invocando al `127.0.0.1:8126` (`DD_AGENT_HOST`). A su vez, el contenedor de Spring Boot manda por `awslogs` el Log al Grupo en CloudWatch para luego correlacionarlo.*

---

## ✅ Resumen del Flujo de Trabajo

1. El usuario de tu app o cliente llama al Endpoint HTTPS.
2. **API Gateway / ALB** intercepta la petición, genera un `X-Amzn-Trace-Id` y lo agrega.
3. El request llega a tu contenedor **Java Spring Boot**.
4. ¡El `AwsTraceIdFilter.java` extrae `X-Amzn-Trace-Id` y lo pone en el Log MDC (`aws.trace_id`)!
5. El **Datadog javaagent** intercepta el framework por byte-code, genera un `dd.trace_id`, lee `X-Amzn-Trace-Id` gracias a la variable `DD_TRACE_HEADER_TAGS` y crea el métrica/trace general en el APM de Datadog. A su vez, inyecta su propio DD Trace ID en tu Log mediante `DD_LOGS_INJECTION=true`.
6. Tu Logger de Spring Boot (`logback-spring.xml`) escupe al stdout algo como:  
   `2026-03-30 14:00:00 INFO [dd.trace_id=987654321 dd.span_id=123654 aws.trace_id=Root=1-5d9d... ] - Request User Authenticated`
7. **CloudWatch Agent** levanta ese log. Ahora, haciendo un Query en CloudWatch Logs usando el Root Trace de AWS, verás en la misma linea el ID de APM de Datadog (`dd.trace_id`), y si buschas en Datadog APM el Trace raíz, tendrás como Tag el `aws.trace_id`.

**¡Trazabilidad distribuida desde AWS hasta el código interno resuelta!**
