# Configuración

> **Fuente:** [kiro.dev/docs/cli/chat/configuration/](https://kiro.dev/docs/cli/chat/configuration/)

---

Kiro CLI puede configurarse en tres ámbitos para adaptarse a tus preferencias y estándares de equipo.

---

## Rutas del archivo de configuración

| Alcance | Ubicación | Descripción |
|---|---|---|
| **Global** | `~/.kiro/` | Aplica a todos los proyectos donde se usa Kiro |
| **Proyecto** | `<raíz-proyecto>/.kiro` | Específico al proyecto |
| **Agente** | `<inicio-usuario\|raíz-proyecto>/.kiro/agents` | Definido en el archivo de configuración del agente |

### Referencia de archivos de configuración

| Archivo | Alcance |
|---|---|
| `~/.kiro/settings/mcp.json` | PCM global |
| `.kiro/settings/mcp.json` | Proyecto MCP |
| `~/.kiro/prompts` | Avisos globales |
| `.kiro/prompts` | Indicaciones del proyecto |
| `~/.kiro/agentes` | Agentes Globales |
| `.kiro/agentes` | Agentes de Proyectos |
| `~/.kiro/dirección` | Dirección Global |
| `.kiro/dirección` | Dirección de Proyectos |
| `~/.kiro/settings/cli.json` | Configuración CLI global |

---

## Resolución de conflictos de configuración

Los conflictos de configuración se resuelven eligiendo la configuración **más cercana al contexto actual**:

> Si tienes una configuración MCP en los archivos `mcp.json` global y del proyecto, cuando chateas en la carpeta del proyecto, se aplica la configuración MCP del proyecto.

**Orden de prioridad:**

```
Agent config  >  Project config  >  Global config
```

> Para servidores MCP, la prioridad es diferente. Ver [prioridad de carga del servidor MCP →] (https://kiro.dev/docs/cli/mcp/#mcp-server-loading-priority)

---

## Configuraciones comunes

Podés gestionar la configuración vía CLI:

```golpecito
# Ver una configuración
configuración de kiro-cli chat.diffTool

# Establecer un ajuste
configuración de kiro-cli chat.diffTool delta
configuración de kiro-cli chat.enableTangentMode verdadero

# Eliminar una configuración (vuelve al valor predeterminado)
configuración de kiro-cli -d chat.diffTool
```