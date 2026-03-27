# Protección de datos

> **Fuente:** [kiro.dev/docs/cli/privacy-and-security/data-protection/](https://kiro.dev/docs/cli/privacy-and-security/data-protection/)

---

## Almacenamiento de datos

Kiro almacena tus preguntas, sus respuestas y contexto adicional (como código) para generar nuevas respuestas a tus solicitudes.

---

## Cifrado de datos

### Cifrado en tránsito

Toda la comunicación entre el cliente Kiro CLI y los servicios de AWS está cifrada usando **TLS (Transport Layer Security)**.

### Cifrado en reposo

Los datos almacenados en la infraestructura de AWS están cifrados en reposo. Los administradores Enterprise pueden configurar opciones adicionales de cifrado desde la Kiro Console.

---

## Procesamiento entre regiones

### Inferencia entre regiones

Para mejorar la disponibilidad y el rendimiento, Kiro puede procesar solicitudes usando infraestructura en múltiples regiones AWS.

### Regiones admitidas

Kiro ofrece inferencia entre regiones en regiones de AWS seleccionadas. Para características experimentales se puede utilizar **inferencia global entre regiones**.

---

## Mejora del servicio

Para ayudar a Kiro a proporcionar información más relevante, AWS puede usar cierto contenido de Kiro — como preguntas que hace, otros inputs, y las respuestas y código que genera — para **mejora del servicio**.

### Contenido utilizado para mejorar el servicio

El contenido puede incluir:
- Indicaciones y preguntas
- Insumos adicionales
- Respuestas generadas
- Código producido

---

## Optar por no compartir datos

Por defecto, Kiro recopila datos de uso, errores, crash reports y otras métricas de usuarios del **Free Tier** y **suscriptores individuales**.

> Los **usuarios Enterprise** son automáticamente excluidos de la recolección de telemetría y contenido por AWS. La configuración de telemetría para Enterprise es controlada por el administrador desde la Kiro Console.

### Optar por no participar en la CLI

```bash
kiro-cli settings telemetry.enabled false
```

### Optar por no participar en el IDE

Vaya a **Configuración → Privacidad** y desmarcar las opciones de uso de datos.

---

## Tipos de telemetría recopilados

| Tipo | Descripción |
|---|---|
| Datos de uso | Comandos usados, frecuencia de uso |
| Errores | Errores y excepciones |
| Informes de fallos | Informe de fallos de la aplicación |
| Métricas | Métricas de rendimiento y latencia |
| Contenido (suscripción voluntaria) | Avisos y respuestas para mejorar el servicio |