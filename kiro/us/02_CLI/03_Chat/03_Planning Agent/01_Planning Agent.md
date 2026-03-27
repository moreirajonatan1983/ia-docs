# Plan Agent

> **Source:** [kiro.dev/docs/cli/chat/planning-agent/](https://kiro.dev/docs/cli/chat/planning-agent/)

---

El **Plan Agent** transforma ideas en planes de implementación estructurados antes de escribir código. Opera en modo **read-only** para mantenerse enfocado en el planeamiento.

---

## Getting Started

| Método | Comando |
|---|---|
| **Keyboard shortcut** | `Shift + Tab` — toggle entre modo plan y ejecución |
| **Slash command** | `/plan` |
| **Con prompt inmediato** | `/plan Build a REST API for user authentication` |

Al activarse, verás el indicador `[plan]` en tu prompt y un mensaje de bienvenida.

---

## Plan Workflow

### 1. Requirements Gathering

El planner te hace preguntas estructuradas para refinar tu idea inicial:

```
[plan] > I want to build a todo app
I understand you want to build a todo app. Let me help plan this.

[1]: What platform should this todo app target?
a. Web Application   b. Mobile App   c. Desktop App   d. CLI Tool

[2]: What's the primary use case?
a. Personal Task Management   b. Team Collaboration   c. Project Management

(Use the chat to answer any subset: e.g. "1=a, 2=b")
```

### 2. Research and Analysis

El planner explora tu codebase y researcha tecnologías relevantes.

### 3. Implementation Plan

Genera un plan detallado paso a paso con objetivos claros:

```
**Implementation Plan - Todo CLI Command**

Problem Statement: Add todo management to existing CLI.

Task 1: Create database schema and models
- Define Todo struct with required fields
- Demo: Can create and query todos in database

Task 2: Implement CLI command structure
- Add todo subcommand with add/list/complete operations
- Demo: CLI accepts todo commands and shows help
```

Cada tarea incluye: objetivos claros, guía de implementación, descripción demo.

### 4. Plan Approval and Handoff

Antes de pasar a ejecución, el planner solicita tu aprobación:

```
[plan] > Does this plan look good, or would you like me to adjust anything?
> Looks great! Let's implement it.

Planning complete! Ready to exit [plan] agent? [y/n]: y
```

El proceso de handoff:
1. Aprobás el plan de implementación
2. Prompt interactivo confirma el cambio al modo ejecución
3. Transición automática al agente anterior
4. El plan completo se pasa al agente de ejecución

---

## Read-Only Design

El Plan Agent opera en modo **read-only** para mantener el foco en el planeamiento. No modifica archivos durante la fase de planning.

---

## Best Practices

1. **Usalo para tareas complejas** — más valioso para implementaciones de múltiples pasos
2. **Respondé las preguntas con detalle** — mejora la calidad del plan
3. **Dejalo explorar** — permití que analice tu codebase existente
4. **Revisá los planes** — asegurate de que el plan coincide con tus expectativas antes del handoff
5. **Iterá** — refiná hasta que el plan sea claro

---

## Example Workflow

```
> /plan Add user authentication to my web app

[plan] > My Understanding: You want to implement user authentication.

[1]: What authentication method do you prefer?
a. Email/Password   b. OAuth   c. Magic Links   d. Multi-factor
> 1=a

[2]: What's your current tech stack?
d. Other - Please specify
> 2=d, I'm using Rust with Axum framework

*Researching Axum authentication patterns...*
*Exploring your existing codebase structure...*

**Implementation Plan - User Authentication System**
[Detailed plan...]

Does this plan look good? > Looks perfect!
Ready to exit [plan] agent? [y/n]: y

[default] > Implement this plan: [Plan transferred to execution agent]
```