# Data Protection

> **Source:** [kiro.dev/docs/cli/privacy-and-security/data-protection/](https://kiro.dev/docs/cli/privacy-and-security/data-protection/)

---

## Data Storage

Kiro almacena tus preguntas, sus respuestas y contexto adicional (como código) para generar nuevas respuestas a tus requests. 

---

## Data Encryption

### Encryption in Transit

Toda la comunicación entre el cliente Kiro CLI y los servicios de AWS está cifrada usando **TLS (Transport Layer Security)**.

### Encryption at Rest

Los datos almacenados en la infraestructura de AWS están cifrados en reposo. Los administradores Enterprise pueden configurar opciones adicionales de cifrado desde la Kiro Console.

---

## Cross-Region Processing

### Cross-Region Inference

Para mejorar disponibilidad y rendimiento, Kiro puede procesar requests usando infraestructura en múltiples regiones AWS.

### Supported Regions

Kiro ofrece cross-region inference en regiones de AWS seleccionadas. Para features experimentales puede usarse **global cross-region inference**.

---

## Service Improvement

Para ayudar a Kiro a proveer información más relevante, AWS puede usar cierto contenido de Kiro — como preguntas que hacés, otros inputs, y las respuestas y código que genera — para **mejora del servicio**.

### Content Used for Service Improvement

El contenido puede incluir:
- Prompts y preguntas
- Inputs adicionales
- Respuestas generadas
- Código producido

---

## Opt Out of Data Sharing

Por defecto, Kiro recolecta datos de uso, errores, crash reports y otras métricas de usuarios del **Free Tier** y **suscriptores individuales**.

> Los **usuarios Enterprise** son automáticamente excluidos de la recolección de telemetría y contenido por AWS. La configuración de telemetría para Enterprise es controlada por el administrador desde la Kiro Console.

### Opting Out in the CLI

```bash
kiro-cli settings telemetry.enabled false
```

### Opting Out in the IDE

Ir a **Settings → Privacy** y desmarcar las opciones de uso de datos.

---

## Types of Telemetry Collected

| Tipo | Descripción |
|---|---|
| Usage data | Comandos usados, frecuencia de uso |
| Errors | Errores y excepciones |
| Crash reports | Reporte de crashes de la aplicación |
| Metrics | Métricas de rendimiento y latencia |
| Content (opt-in) | Prompts y respuestas para mejora del servicio |