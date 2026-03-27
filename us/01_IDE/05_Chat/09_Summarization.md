# Summarization

> **Source:** [kiro.dev/docs/chat/summarization/](https://kiro.dev/docs/chat/summarization/)

---

## Overview

Todos los modelos de lenguaje tienen un "context window" — la cantidad máxima de texto que el modelo puede manejar al mismo tiempo. El tamaño varía según el modelo.

Cuando tenés una conversación con Kiro, recuerda y envía todos los mensajes anteriores como contexto al modelo. A medida que la conversación se alarga, eventualmente se acerca al límite del context window.

---

## Automatic Summarization

Cuando el uso del contexto alcanza el **80% del límite del modelo**, Kiro **automáticamente resumirá** todos los mensajes de la conversación para que la longitud del contexto vuelva a estar por debajo del límite.

Podés monitorear el uso actual del contexto con el **medidor de uso de contexto** en el panel del chat.

---

## Context Usage Meter

El medidor en el panel del chat muestra en tiempo real qué porcentaje del context window del modelo está siendo utilizado. Usalo para anticiparte a la summarización automática antes de que ocurra.

---

## Related

- [Checkpoints →](./08_Checkpoints.md) — Los checkpoints pueden verse afectados por la summarización
- [Autopilot →](./02_Autopilot.md) — En Autopilot, la summarización ocurre más frecuentemente en tareas largas