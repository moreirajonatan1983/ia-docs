# Creating Custom Agents

> **Source:** [kiro.dev/docs/cli/custom-agents/creating/](https://kiro.dev/docs/cli/custom-agents/creating/)

---

Los custom agents te permiten crear asistentes de IA especializados para workflows específicos.

---

## Quick Start

Desde una sesión de chat de Kiro CLI:

```
> /agent create
✔ Enter agent name: · backend-specialist
✔ Enter agent description: · You are a specialist in backend coding practices
✔ Agent scope · Local (current workspace)
Select MCP servers: markdown-downloader (node), code-analysis (uv)
✓ Agent 'backend-specialist' has been created and saved successfully!
```

También podés proveer nombre y opciones inline:

```
> /agent create backend-specialist -D "Backend coding specialist" -m code-analysis
```

O desde el terminal directamente:

```bash
kiro-cli agent create backend-specialist
```

> `/agent generate` es un alias de `/agent create`. Ambos comandos se comportan de manera idéntica.

---

## Options

| Flag | Descripción | Disponible en |
|---|---|---|
| `--directory` | Dónde guardar el agente | Ambos |
| `--from` | Basar en un agente existente | Ambos |
| `--manual` | Modo de creación manual (editor) | Ambos |
| `--description` / `-D` | Descripción del agente | Solo AI-assisted |
| `--mcp-server` / `-m` | MCP server a incluir | Solo AI-assisted |

> `--description` y `--mcp-server` no pueden usarse con `--manual` ni `--from`.

### Directory Values

| Valor | Ubicación |
|---|---|
| `workspace` | `.kiro/agents/` (proyecto actual) |
| `global` | `~/.kiro/agents/` (todos los proyectos) |
| `./path` o `/path` | Ruta personalizada |

Sin `--directory`, los agentes se guardan en el directorio global (`~/.kiro/agents/`).

### Manual Creation Mode

Para definir la configuración vos mismo en un editor:

```
> /agent create my-agent --manual
```

Para basar un nuevo agente en uno existente:

```
> /agent create my-agent --from backend-specialist
```

---

## Agent Configuration File

Los custom agents se definen con archivos de configuración JSON:

```json
{
  "name": "my-agent",
  "description": "A custom agent for my workflow",
  "tools": ["read", "write"],
  "allowedTools": ["read"],
  "resources": [
    "file://README.md",
    "file://.kiro/steering/**/*.md",
    "skill://.kiro/skills/**/SKILL.md"
  ],
  "prompt": "You are a helpful coding assistant",
  "model": "claude-sonnet-4"
}
```

---

## Using Your Custom Agent

```
> /agent swap
❯ rust-developer-agent
  kiro_default
  backend-specialist
```

Después de seleccionar:
```
✔ Choose one of the following agents · backend-specialist
[backend-specialist] >
```

O iniciá directamente con tu agente:
```bash
kiro-cli --agent my-agent
```