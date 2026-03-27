# Agent Notifications

> **Source:** [kiro.dev/docs/chat/notifications/](https://kiro.dev/docs/chat/notifications/)

---

Las notificaciones del agente mantienen informado sobre el progreso y las acciones del agente Kiro, especialmente cuando trabaja en segundo plano o en tareas de larga duración.

---

## Overview

Cuando Kiro trabaja en modo Autopilot ejecutando tareas complejas, las notificaciones te permiten:

- Saber cuándo completó una tarea o fase
- Ser alertado si el agente encuentra un problema y necesita tu input
- Monitorear el progreso sin necesidad de mantener el chat en foco

---

## Notification Types

- **Task complete:** El agente terminó un turno o tarea
- **Approval required:** El agente necesita tu aprobación para continuar
- **Error:** El agente encontró un error que no puede resolver solo
- **Background process:** Un dev server o proceso en segundo plano reporta estado

---

## Related

- [Autopilot →](./02_Autopilot.md) — Modo autónomo donde las notificaciones son más relevantes
- [Dev Servers →](./05_Dev servers.md) — Procesos en segundo plano que generan notificaciones
- [Checkpoints →](./08_Checkpoints.md) — Puntos de control para revertir cambios