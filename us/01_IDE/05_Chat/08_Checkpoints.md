# Checkpoints

![Checkpoints](https://kiro.dev/videos/checkpoints.mp4)


> **Source:** [kiro.dev/docs/chat/checkpoints/](https://kiro.dev/docs/chat/checkpoints/)

---

Los checkpoints permiten deshacer cambios realizados por Kiro a través de múltiples turnos, incluyendo tanto cambios en archivos como adiciones de contexto.

---

## Overview

Cada vez que el agente Kiro modifica uno o más archivos y completa su turno, aparece inmediatamente arriba del cuadro de input del chat la opción de **Revert** los cambios realizados.

---

## Reverts vs. Checkpoints

| | Revert | Checkpoint |
|---|---|---|
| **Alcance temporal** | Solo el último turno del agente | Múltiples turnos |
| **Qué deshace** | Solo cambios en archivos | Cambios en archivos **y** adiciones de contexto |
| **Cómo acceder** | Botón "Revert" sobre el input | Selector de checkpoint en el historial |

---

## How to Use Checkpoints

1. Kiro crea un checkpoint automáticamente antes de cada turno que modifica archivos
2. Para revertir a un checkpoint anterior, buscá el icono de checkpoint en el historial del chat
3. Seleccioná el checkpoint al que querés volver
4. Kiro deshará todos los cambios en archivos y eliminará las adiciones de contexto realizadas desde ese punto

---

## Best Practices

- Usá **Revert** para deshacer solo el último paso
- Usá **Checkpoints** cuando querés volver a un estado anterior luego de múltiples pasos del agente
- Los checkpoints son especialmente útiles en workflow de Autopilot donde el agente ejecuta muchos cambios seguidos

---

## Related

- [Autopilot →](./02_Autopilot.md) — donde los checkpoints son más útiles
- [Summarization →](./09_Summarization.md) — gestión del contexto de conversación