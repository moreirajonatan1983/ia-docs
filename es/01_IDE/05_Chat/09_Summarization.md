# Resumen

> **Fuente:** [kiro.dev/docs/chat/summarization/](https://kiro.dev/docs/chat/summarization/)

---

## Descripción general

Todos los modelos de lenguaje tienen una "ventana de contexto" — la cantidad máxima de texto que el modelo puede manejar al mismo tiempo. El tamaño varía según el modelo.

Cuando tengas una conversación con Kiro, recuerda y envía todos los mensajes anteriores como contexto al modelo. A medida que la conversación se alarga, eventualmente se acerca al límite de la ventana de contexto.

---

## Resumen automático

Cuando el uso del contexto alcanza el **80% del límite del modelo**, Kiro **automáticamente resumirá** todos los mensajes de la conversación para que la longitud del contexto vuelva a estar por debajo del límite.

Podés monitorear el uso actual del contexto con el **medidor de uso de contexto** en el panel del chat.

---

## Medidor de uso de contexto

El medidor en el panel del chat muestra en tiempo real qué porcentaje de la ventana de contexto del modelo está siendo utilizado. Usalo para anticiparte a la resumen automática antes de que ocurra.

---

## Relacionado

- [Checkpoints →](./08_Checkpoints.md) — Los checkpoints pueden verse afectados por la resumen
- [Autopilot →](./02_Autopilot.md) — En Autopilot, la resumen ocurre más frecuentemente en tareas largas