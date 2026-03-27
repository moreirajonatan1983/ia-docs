# Notificaciones de agentes

> **Fuente:** [kiro.dev/docs/chat/notifications/](https://kiro.dev/docs/chat/notifications/)

---

Las notificaciones del agente se mantienen informadas sobre el progreso y las del agente Kiro, especialmente cuando trabaja en segundo plano o en tareas de larga duración.

---

## Descripción general

Cuando Kiro trabaja en modo Autopilot ejecutando tareas complejas, las notificaciones te permiten:

- Saber cuándo completó una tarea o fase
- Ser alertado si el agente encuentra un problema y necesita su información
- Monitorear el progreso sin necesidad de mantener el chat en foco

---

## Tipos de notificación

| Tipo | Cuándo ocurre |
|---|---|
| **Tarea completa** | El agente terminó un turno o tarea |
| **Se requiere aprobación** | El agente necesita tu aprobación para continuar |
| **Error** | El agente encontró un error que no puede resolver solo |
| **Proceso en segundo plano** | Un servidor de desarrollo o proceso en segundo plano reporta estado |

---

## Relacionado

- [Autopilot →](./02_Autopilot.md) — Modo autónomo donde las notificaciones son más relevantes
- [Dev Servers →](./05_Dev servers.md) — Procesos en segundo plano que generan notificaciones
- [Checkpoints →](./08_Checkpoints.md) — Puntos de control para revertir cambios