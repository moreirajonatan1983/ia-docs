# Configuration

> **Source:** [kiro.dev/docs/cli/chat/configuration/](https://kiro.dev/docs/cli/chat/configuration/)

---

Kiro CLI puede configurarse en tres scopes para adaptarse a tus preferencias y estándares de equipo.

---

## Configuration File Paths

| Scope | Ubicación | Descripción |
|---|---|---|
| **Global** | `~/.kiro/` | Aplica a todos los proyectos donde se usa Kiro |
| **Project** | `<project-root>/.kiro` | Específico al proyecto |
| **Agent** | `<user-home\|project-root>/.kiro/agents` | Definido en el archivo de configuración del agente |

### Config Files Reference

| Archivo | Scope |
|---|---|
| `~/.kiro/settings/mcp.json` | Global MCP |
| `.kiro/settings/mcp.json` | Project MCP |
| `~/.kiro/prompts` | Global Prompts |
| `.kiro/prompts` | Project Prompts |
| `~/.kiro/agents` | Global Agents |
| `.kiro/agents` | Project Agents |
| `~/.kiro/steering` | Global Steering |
| `.kiro/steering` | Project Steering |
| `~/.kiro/settings/cli.json` | Global CLI Settings |

---

## Resolving Configuration Conflicts

Los conflictos de configuración se resuelven eligiendo la configuración **más cercana al contexto actual**:

> Si tenés una configuración MCP en los archivos `mcp.json` global y del proyecto, cuando chateás en la carpeta del proyecto, se aplica la configuración MCP del proyecto.

**Priority order:**

```
Agent config  >  Project config  >  Global config
```

> Para servidores MCP, la prioridad es diferente. Ver [MCP server loading priority →](https://kiro.dev/docs/cli/mcp/#mcp-server-loading-priority)

---

## Common Settings

Podés gestionar settings vía CLI:

```bash
# Ver un setting
kiro-cli settings chat.diffTool

# Establecer un setting
kiro-cli settings chat.diffTool delta
kiro-cli settings chat.enableTangentMode true

# Eliminar un setting (vuelve al default)
kiro-cli settings -d chat.diffTool
```