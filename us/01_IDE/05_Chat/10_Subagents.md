# Subagents

![Subagents](https://kiro.dev/videos/subagents.mp4)


> **Source:** [kiro.dev/docs/chat/subagents/](https://kiro.dev/docs/chat/subagents/)

---

Los subagentes permiten a Kiro ejecutar tareas en paralelo y delegar trabajo especializado a agentes apropiados.

---

## Overview

Kiro puede crear subagentes para manejar tareas complejas de forma independiente. Cada subagente opera con su propio contexto y conjunto de herramientas, reportando resultados al agente principal.

---

## Custom Subagents

Podés definir tu propio agente personalizado creando un archivo Markdown (`.md`) en:

- `~/.kiro/agents/` — scope global (disponible en todos los workspaces)
- `<workspace>/.kiro/agents/` — scope de workspace (solo en ese proyecto)

El prompt del agente va en el cuerpo del archivo. Los atributos adicionales se definen como YAML front matter.

### Ejemplo: Code Reviewer Agent

Creá `~/.kiro/agents/code-reviewer.md`:

```markdown
---
name: code-reviewer
description: Expert code review assistant.
tools: ["read", "@context7"]
model: claude-sonnet-4
---

You are a senior code reviewer.

## Your Responsibilities
- Review code for correctness, performance, and security
- Suggest improvements with examples
- Check for common anti-patterns
```

### Invocation

Kiro invoca automáticamente el subagente cuando detecta que la tarea encaja con su descripción, o podés invocarlo explícitamente:

```
> Use the code-reviewer agent to review this PR
```

### Attributes (YAML front matter)

| Campo | Descripción |
|---|---|
| `name` | Nombre único del agente |
| `description` | Descripción de cuándo usar este agente (usada para auto-detección) |
| `tools` | Lista de herramientas disponibles para el agente |
| `model` | Modelo AI a utilizar |

---

## Related

- [Custom Agents Reference →](https://kiro.dev/docs/chat/custom-agents/)
- [Autopilot →](./02_Autopilot.md) — Los subagentes funcionan principalmente en modo Autopilot