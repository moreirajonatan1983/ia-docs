# Delegate

> **Source:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#delegate)

> ⚠️ **Feature experimental** — puede cambiar en futuras versiones.

---

## Overview

Delegate permite lanzar y gestionar **procesos de tareas asíncronos**, ejecutando sesiones de chat de Kiro con agentes específicos en paralelo, en segundo plano.

**Habilitar:**
```bash
kiro-cli settings chat.enableDelegate true
```

---

## Features

- Lanzar tareas en background usando lenguaje natural
- Ejecutar sesiones de chat paralelas con agentes específicos
- Monitorear el progreso de las tareas de forma independiente
- Flujo de aprobación del agente para seguridad

---

## Usage

```
# Lanzar una tarea en background con lenguaje natural
> Can you create a background task to analyze the performance of our API endpoints?

# El agente pide aprobación, luego ejecuta en background
✔ Launching background task: API Performance Analysis

# Verificar el estado
> Check the status of my API analysis task

# Ver resultados
> Show me the results from the background analysis
```

---

## Use Cases

- **Análisis de código largo** — Ejecutar en background mientras seguís trabajando
- **Tests extensos** — Correr suites de tests sin bloquear la sesión
- **Generación de documentación** — Generar docs de múltiples archivos en paralelo
- **Migraciones** — Tareas pesadas que llevan mucho tiempo

---

## Security

Delegate incluye un **flujo de aprobación** antes de ejecutar cada tarea. Revisá siempre qué va a hacer el agente antes de aprobar.

---

## Learn More

- [Experimental features overview →](https://kiro.dev/docs/cli/experimental/)
- [Full Delegate docs →](https://kiro.dev/docs/cli/experimental/delegate)