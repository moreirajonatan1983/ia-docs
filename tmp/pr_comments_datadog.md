# Pull Request Documentation / Documentación del PR

## 🇪🇸 Versión en Español

### 🌿 Nombre del Branch (Rama)
`feature/DEV-XXXX-trazabilidad-datadog-aws`
*(Reemplaza XXXX por el ID real de tu ticket asignado)*

### 📝 Título del Pull Request (PR)
`feat(observabilidad): habilitar trazabilidad cruzada bidireccional entre AWS CloudWatch y Datadog APM`

### 💬 Descripción del Commit y PR

**Título del Commit:**
`feat(observabilidad): correlation traces aws y datadog en logs mdc`

**Cuerpo del Commit / Descripción del PR:**
```text
Implementa la inyección y lectura de variables de trazabilidad (Trace IDs y Span IDs) para correlacionar los logs de CloudWatch con Datadog APM en la arquitectura serverless (ECS Fargate).

Cambios principales:
- application.yaml: Se modifica el logging.pattern para forzar la impresión de las variables del MDC %X{dd.trace_id}, %X{dd.span_id} (originadas por el Java Agent) y %X{aws.trace_id}.
- OptionalCompanyHeaderInterceptor.java: Se agrega la lectura del header nativo del Ingress de AWS (X-Amzn-Trace-Id) dentro del método preHandle para inyectarlo al contexto MDC de Spring Boot (aws.trace_id).
- No requiere modificación en el método afterCompletion dado que el MDC.clear() preexistente ya previene la filtración de variables entre hilos del servidor embebido.

Dependencia de Infraestructura: 
Requiere validar que el contenedor inicie con -Ddd.logs.injection=true y -Ddd.trace.header.tags="X-Amzn-Trace-Id:aws.trace_id" a través del Dockerfile o Terraform.
```

---

## 🇬🇧 English Version

### 🌿 Branch Name
`feature/DEV-XXXX-cross-traceability-aws-datadog`
*(Replace XXXX with your actual ticket ID)*

### 📝 Pull Request Title
`feat(observability): enable cross-traceability between AWS CloudWatch and Datadog APM`

### 💬 Commit Message & PR Description

**Commit Title:**
`feat(observability): correlate aws and datadog traces in mdc logs`

**Commit Body / PR Description:**
```text
Implements the setup and injection of traceability variables (Trace IDs and Span IDs) to correlate CloudWatch logs with Datadog APM in our ECS Serverless architecture.

Main changes:
- application.yaml: Modified the logging.pattern to force the printing of MDC variables %X{dd.trace_id}, %X{dd.span_id} (originated by the Datadog Java Agent), and %X{aws.trace_id}.
- OptionalCompanyHeaderInterceptor.java: Added logic to read the native AWS Ingress header (X-Amzn-Trace-Id) inside the preHandle method, injecting it into the Spring Boot MDC context as aws.trace_id.
- No modifications were required in the afterCompletion method since the pre-existing MDC.clear() already prevents variable leakage between threads on the embedded application server.

Infrastructure Dependency:
Ensure the ECS container starts with -Ddd.logs.injection=true and -Ddd.trace.header.tags="X-Amzn-Trace-Id:aws.trace_id" via Dockerfile (CMD) or Terraform var.container_def block.
```
