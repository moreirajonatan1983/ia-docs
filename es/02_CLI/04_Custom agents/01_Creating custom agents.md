# Creando agentes personalizados

> **Fuente:** [kiro.dev/docs/cli/custom-agents/creating/](https://kiro.dev/docs/cli/custom-agents/creating/)

---

Los agentes personalizados te permiten crear asistentes de IA especializados para flujos de trabajo específicos.

---

## Inicio rápido

Desde una sesión de chat de Kiro CLI:

```
> /agent create
✔ Enter agent name: · backend-specialist
✔ Enter agent description: · You are a specialist in backend coding practices
✔ Agent scope · Local (current workspace)
Select MCP servers: markdown-downloader (node), code-analysis (uv)
✓ Agent 'backend-specialist' has been created and saved successfully!
```

También podés proporcionar nombre y opciones en línea:

```
> /agent create backend-specialist -D "Backend coding specialist" -m code-analysis
```

O desde la terminal directamente:

```bash
kiro-cli agent create backend-specialist
```

> `/agent generate` es un alias de `/agent create`. Ambos comandos se comportan de manera idéntica.

---

## Opciones

| Bandera | Descripción | Disponible en |
|---|---|---|
| `--directorio` | Dónde guardar el agente | Ambos |
| `--de` | Basar en un agente existente | Ambos |
| `--manual` | Manual de modo de creación (editor) | Ambos |
| `--descripción` / `-D` | Descripción del agente | Solo asistido por IA |
| `--mcp-server` / `-m` | Servidor MCP a incluir | Solo asistido por IA |

> `--description` y `--mcp-server` no pueden usarse con `--manual` ni `--from`.

### Valores del directorio

| Valor | Ubicación |
|---|---|
| `espacio de trabajo` | `.kiro/agents/` (proyecto actual) |
| `global` | `~/.kiro/agents/` (todos los proyectos) |
| `./ruta` o `/ruta` | Ruta personalizada |

Sin `--directory`, los agentes se guardan en el directorio global (`~/.kiro/agents/`).

### Modo de creación manual

Para definir la configuración usted mismo en un editor:

```
> /agent create my-agent --manual
```

Para basar un nuevo agente en uno existente:

```
> /agent create my-agent --from backend-specialist
```

---

## Archivo de configuración del agente

Los agentes personalizados se definen con archivos de configuración JSON:

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

## Usando su agente personalizado

```
> /agent swap
❯ rust-developer-agent
  kiro_default
  backend-specialist
```

Después de seleccionar:
```
✔ Elija uno de los siguientes agentes · especialista en backend
[especialista en backend] >
```

O iniciará directamente con tu agente:
```golpecito
kiro-cli --agente mi-agente
```