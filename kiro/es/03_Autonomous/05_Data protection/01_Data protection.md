# Protección de datos — Agente autónomo

> **Fuente:** [kiro.dev/docs/autonomous-agent/data-protection/](https://kiro.dev/docs/autonomous-agent/data-protection/)

---

## Modelo de responsabilidad compartida

El [Shared Responsibility Model de AWS](https://aws.amazon.com/compliance/shared-responsibility-model/) aplica a la protección de datos en el Agente Autónomo Kiro:

| AWS es responsable de | Vos sos responsable de |
|---|---|
| Proteger la infraestructura global de la nube de AWS | Mantener control sobre tu contenido en esa infraestructura |
| Seguridad física de centros de datos | Configuración de seguridad y tareas de gestión de los servicios AWS que usamos |

Para obtener más información, consulte [Preguntas frecuentes sobre privacidad de datos →](https://aws.amazon.com/compliance/data-privacy-faq/).

---

## Almacenamiento de datos

El Agente Autónomo El Kiro almacena:
- Descripciones de tareas
- Mensajes de chat
- Cambios de código
- Contexto adicional

Esta información se usa para ejecutar tareas y generar respuestas.

### Regiones de AWS donde se almacena el contenido

> **Durante el Preview:** Todo el contenido del Kiro Autónomo Agente (descripciones de tareas, mensajes de chat, cambios de código) se almacena en la región **US East (N. Virginia)**.

Con inferencia entre regiones, tu contenido puede procesarse en una región diferente dentro de los Estados Unidos.

---

## Procesamiento entre regiones

Para mejorar la disponibilidad y el rendimiento, Kiro puede procesar solicitudes usando infraestructura en múltiples regiones de AWS dentro de los Estados Unidos.

** Regiones soportadas para inferencia entre regiones del Agente Autónomo: **  
Este de EE.UU. (N. Virginia), Este de EE.UU. (Ohio), Oeste de EE.UU. (Oregón) *(y otras regiones de EE.UU. según disponibilidad)*

---

## Cifrado de datos

### Cifrado en tránsito

Toda la comunicación entre:
- Clientes y el Kiro Agente Autónomo
- El Kiro Agente Autónomo y sus dependencias aguas abajo

está usando conexiones protegidas **TLS 1.2 o superior**.

### Cifrado en reposo

El Agente Autónomo de Kiro cifra tus datos usando **claves de cifrado propiedad de AWS** de AWS Key Management Service (AWS KMS). No necesitás tomar ninguna acción para proteger las claves administradas que cifran tus datos.

Ver [Claves propiedad de AWS →](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#aws-owned-cmk) para más información.

---

## Mejora del servicio

Para ayudar a Kiro a proporcionar la información más relevante, AWS puede usar cierto contenido del Kiro Autónomo Agente para **mejora del servicio**.

### Contenido utilizado para mejorar el servicio

El contenido que Kiro puede usar incluye:
- Descripciones de tareas
- Mensajes de chat
- Otros insumos que proporcionalás
- Respuestas y código que genera Kiro

Este contenido puede usarse para: mejorar respuestas a preguntas comunes, corregir problemas operativos de Kiro, Debug o entrenamiento de modelos.

---

## Optar por no compartir datos

Por defecto, el Agente Autónomo Kiro recopila contenido para mejorar el servicio.

### Cómo darse de baja

1. Navegá a [app.kiro.dev/agent/settings](https://app.kiro.dev/agent/settings)
2. Navegar a la sección **Recopilación de datos**
3. Desactivar **"Permitir que AWS utilice el contenido de su agente autónomo Kiro para mejorar el servicio"**

---

## Relacionado

- [Integración de GitHub →](./04_GitHub.md)
- [Agente Sandbox →](./03_Agent%20Sandbox/)
- [Política de privacidad de AWS →](https://aws.amazon.com/privacy/)