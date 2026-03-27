# Data Protection — Autonomous Agent

> **Source:** [kiro.dev/docs/autonomous-agent/data-protection/](https://kiro.dev/docs/autonomous-agent/data-protection/)

---

## Shared Responsibility Model

El [Shared Responsibility Model de AWS](https://aws.amazon.com/compliance/shared-responsibility-model/) aplica a la protección de datos en el Kiro Autonomous Agent:

| AWS es responsable de | Vos sos responsable de |
|---|---|
| Proteger la infraestructura global de AWS Cloud | Mantener control sobre tu contenido en esa infraestructura |
| Seguridad física de data centers | Configuración de seguridad y tareas de gestión de los servicios AWS que usás |

Para más información, ver [Data Privacy FAQ →](https://aws.amazon.com/compliance/data-privacy-faq/).

---

## Data Storage

El Kiro Autonomous Agent almacena:
- Descripciones de tareas
- Mensajes de chat
- Cambios de código
- Contexto adicional

Esta información se usa para ejecutar tareas y generar respuestas.

### AWS Regions Where Content is Stored

> **Durante el Preview:** Todo el contenido del Kiro Autonomous Agent (descripciones de tareas, mensajes de chat, cambios de código) se almacena en la región **US East (N. Virginia)**.

Con cross-region inferencing, tu contenido puede procesarse en una región diferente dentro de los Estados Unidos.

---

## Cross-Region Processing

Para mejorar disponibilidad y rendimiento, Kiro puede procesar requests usando infraestructura en múltiples regiones de AWS dentro de los Estados Unidos.

**Regiones soportadas para cross-region inference del Autonomous Agent:**  
US East (N. Virginia), US East (Ohio), US West (Oregon) *(y otras regiones de EE.UU. según disponibilidad)*

---

## Data Encryption

### Encryption in Transit

Toda la comunicación entre:
- Clientes y el Kiro Autonomous Agent
- El Kiro Autonomous Agent y sus dependencias downstream

está protegida usando conexiones **TLS 1.2 o superior**.

### Encryption at Rest

El Kiro Autonomous Agent cifra tus datos usando **AWS owned encryption keys** de AWS Key Management Service (AWS KMS). No necesitás tomar ninguna acción para proteger las managed keys que cifran tus datos.

Ver [AWS owned keys →](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#aws-owned-cmk) para más información.

---

## Service Improvement

Para ayudar a Kiro a proveer la información más relevante, AWS puede usar cierto contenido del Kiro Autonomous Agent para **mejora del servicio**.

### Content Used for Service Improvement

El contenido que Kiro puede usar incluye:
- Descripciones de tareas
- Mensajes de chat
- Otros inputs que proporcionás
- Respuestas y código que Kiro genera

Este contenido puede usarse para: mejorar respuestas a preguntas comunes, corregir problemas operacionales de Kiro, debugging, o entrenamiento de modelos.

---

## Opt Out of Data Sharing

Por defecto, el Kiro Autonomous Agent recopila contenido para mejora del servicio.

### How to Opt Out

1. Ir a [app.kiro.dev/agent/settings](https://app.kiro.dev/agent/settings)
2. Navegar a la sección **Data collection**
3. Desactivar **"Allow AWS to use your Kiro autonomous agent content for service improvement"**

---

## Related

- [GitHub integration →](./04_GitHub.md)
- [Agent Sandbox →](./03_Agent%20Sandbox/)
- [AWS Privacy Policy →](https://aws.amazon.com/privacy/)