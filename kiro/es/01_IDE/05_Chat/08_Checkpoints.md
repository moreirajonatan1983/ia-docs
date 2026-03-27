# puntos de control

![Puntos de control](https://kiro.dev/videos/checkpoints.mp4)

> **Fuente:** [kiro.dev/docs/chat/checkpoints/](https://kiro.dev/docs/chat/checkpoints/)

---

Los puntos de control permiten realizar cambios realizados por Kiro a través de múltiples turnos, incluyendo tanto cambios en archivos como adiciones de contexto.

---

## Descripción general

Cada vez que el agente Kiro modifica uno o más archivos y completa su turno, aparece inmediatamente arriba del cuadro de entrada del chat la opción de **Revertir** los cambios realizados.

---

## Reversiones frente a puntos de control

| | Revertir | Punto de control |
|---|---|---|
| **Alcance temporal** | Solo el último turno del agente | Múltiples turnos |
| **Qué deshace** | Solo cambios en archivos | Cambios en archivos **y** adiciones de contexto |
| **Cómo acceder** | Botón "Revertir" sobre la entrada | Selector de punto de control en el historial |

---

## Cómo utilizar los puntos de control

1. Kiro crea un checkpoint automáticamente antes de cada turno que modifica archivos
2. Para revertir a un checkpoint anterior, busque el icono de checkpoint en el historial del chat
3. Selecciona el checkpoint al que quieres volver
4. Kiro deshará todos los cambios en archivos y eliminará las adiciones de contexto realizadas desde ese punto

---

## Mejores prácticas

- Usá **Revert** para deshacer solo el último paso
- Usá **Checkpoints** cuando querés volver a un estado anterior luego de Múltiples pasos del agente
- Los puntos de control son especialmente útiles en el flujo de trabajo de Autopilot donde el agente ejecuta muchos cambios seguidos

---

## Relacionado

- [Autopilot →](./02_Autopilot.md) — donde los puntos de control son más útiles
- [Resumen →](./09_Summarization.md) — gestión del contexto de conversación