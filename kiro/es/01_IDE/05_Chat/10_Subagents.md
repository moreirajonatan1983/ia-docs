# Subagentes

<video src="https://kiro.dev/videos/subagents.mp4" controls autoplay muted loop playsinline width="100%" title="Subagentes"></video>

> **Fuente:** [kiro.dev/docs/chat/subagents/](https://kiro.dev/docs/chat/subagents/)

---

Los subagentes permiten a Kiro ejecutar tareas en paralelo y delegar trabajo especializado a agentes apropiados.

---

## Descripción general

Kiro puede crear subagentes para manejar tareas complejas de forma independiente. Cada subagente opera con su propio contexto y conjunto de herramientas, reportando resultados al agente principal.

---

## Subagentes personalizados

Podés definir tu propio agente personalizado creando un archivo Markdown (`.md`) en:

- `~/.kiro/agents/` — alcance global (disponible en todos los espacios de trabajo)
- `<workspace>/.kiro/agents/` — alcance del espacio de trabajo (solo en ese proyecto)

El aviso del agente va en el cuerpo del archivo. Los atributos adicionales se definen como materia frontal de YAML.

### Ejemplo: Agente revisor de código

Crear `~/.kiro/agents/code-reviewer.md`:

```markdown
---
nombre: revisor de código
Descripción: Asistente experto en revisión de código.
herramientas: ["leer", "@ contexto7"]
modelo: claude-soneto-4
---

Eres un revisor de código senior.

## Tus responsabilidades
- Revisar el código para comprobar su corrección, rendimiento y seguridad.
- Sugerir mejoras con ejemplos.
- Verificar antipatrones comunes
```

### Invocación

Kiro invoca automáticamente el subagente cuando detecta que la tarea encaja con su descripción, o podés invocarlo explícitamente:

```
> Use the code-reviewer agent to review this PR
```

### Atributos (antecedentes de YAML)

| Campo | Descripción |
|---|---|
| `nombre` | Nombre único del agente |
| `descripción` | Descripción de cuándo usar este agente (usada para auto-detección) |
| `herramientas` | Lista de herramientas disponibles para el agente |
| `modelo` | Modelo AI para utilizar |

---

## Relacionado

- [Referencia de agentes personalizados →](https://kiro.dev/docs/chat/custom-agents/)
- [Autopilot →](./02_Autopilot.md) — Los subagentes funcionan principalmente en modo Autopilot