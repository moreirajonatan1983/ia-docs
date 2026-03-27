# Settings Reference

> **Source:** [kiro.dev/docs/cli/reference/settings/](https://kiro.dev/docs/cli/reference/settings/)

---

## Accessing Settings

```bash
kiro-cli settings list                          # Settings actuales
kiro-cli settings list --all                    # Todos los disponibles
kiro-cli settings <key>                         # Ver valor de un setting
kiro-cli settings <key> <value>                 # Setear un setting
kiro-cli settings --delete <key>                # Eliminar un setting
kiro-cli settings open                          # Abrir archivo en editor
kiro-cli settings list --format json-pretty     # Output JSON
```

**Archivo de settings:** `~/.kiro/settings/cli.json`

---

## Settings Reference

### Telemetry and Privacy

| Setting | Ejemplo | Descripción |
|---|---|---|
| `telemetry.enabled` | `true` | Habilitar/deshabilitar telemetría |
| `telemetryClientId` | `"client-123"` | ID de cliente para telemetría |

```bash
kiro-cli settings telemetry.enabled false    # Deshabilitar telemetría
```

---

### Chat Interface

| Setting | Ejemplo | Descripción |
|---|---|---|
| `chat.defaultModel` | `"claude-3-sonnet"` | Modelo por defecto |
| `chat.defaultAgent` | `"my-agent"` | Agente por defecto |
| `chat.diffTool` | `"delta"` | Herramienta diff externa |
| `chat.greeting.enabled` | `false` | Mostrar/ocultar saludo inicial |
| `chat.editMode` | `true` | Modo edición inline |
| `chat.enableNotifications` | `true` | Notificaciones del sistema |
| `chat.disableMarkdownRendering` | `false` | Deshabilitar render de Markdown |
| `chat.disableAutoCompaction` | `true` | Deshabilitar compactación automática |
| `compaction.excludeMessages` | `2` | Mensajes a excluir de compactación |
| `compaction.excludeContextWindowPercent` | `2` | % de ventana de contexto a excluir |
| `chat.enablePromptHints` | `false` | Mostrar hints de prompts |
| `chat.enableHistoryHints` | `true` | Mostrar hints del historial |
| `chat.uiMode` | `"compact"` | Modo UI (`compact` / `default`) |
| `chat.enableContextUsageIndicator` | `true` | Indicador de uso de contexto |

---

### Knowledge Base (Experimental)

| Setting | Ejemplo | Descripción |
|---|---|---|
| `chat.enableKnowledge` | `true` | Habilitar knowledge base |
| `knowledge.defaultIncludePatterns` | `'["*.py", "*.js"]'` | Patrones de archivos a incluir |
| `knowledge.defaultExcludePatterns` | `'["*.log", "node_modules"]'` | Patrones a excluir |
| `knowledge.maxFiles` | `1000` | Máximo de archivos a indexar |
| `knowledge.chunkSize` | `512` | Tamaño de chunk para indexado |
| `knowledge.chunkOverlap` | `50` | Overlap entre chunks |
| `knowledge.indexType` | `"fast"` | Tipo de índice: `"best"` / `"fast"` |

---

### Key Bindings

| Setting | Ejemplo | Descripción |
|---|---|---|
| `chat.skimCommandKey` | `"f"` | Tecla para skim mode |
| `chat.autocompletionKey` | `"Tab"` | Tecla de autocompletado |
| `chat.tangentModeKey` | `"t"` | Tecla para tangent mode |
| `chat.delegateModeKey` | `"d"` | Tecla para delegate mode |

---

### Feature Toggles (Experimental)

| Setting | Comando | Descripción |
|---|---|---|
| `chat.enableThinking` | `kiro-cli settings chat.enableThinking true` | Thinking tool |
| `chat.enableTangentMode` | `kiro-cli settings chat.enableTangentMode true` | Tangent mode |
| `chat.enableTodoList` | `kiro-cli settings chat.enableTodoList true` | TODO lists |
| `chat.enableCheckpoint` | `kiro-cli settings chat.enableCheckpoint true` | Checkpointing |
| `chat.enableDelegate` | `kiro-cli settings chat.enableDelegate true` | Delegate tasks |
| `introspect.tangentMode` | `kiro-cli settings introspect.tangentMode true` | Tangent en introspect |

---

### API and Service

| Setting | Ejemplo | Descripción |
|---|---|---|
| `api.timeout` | `30` | Timeout en segundos para requests a la API |

---

### Model Context Protocol (MCP)

| Setting | Ejemplo | Descripción |
|---|---|---|
| `mcp.initTimeout` | `10` | Timeout de inicialización del servidor MCP |
| `mcp.noInteractiveTimeout` | `5` | Timeout en modo no-interactivo |
| `mcp.loadedBefore` | `true` | Flag de inicialización previa |

---

## Common Configuration Examples

### Basic Setup

```bash
kiro-cli settings telemetry.enabled false
kiro-cli settings chat.defaultModel "claude-3-sonnet"
kiro-cli settings chat.greeting.enabled false
```

### Enable Experimental Features

```bash
kiro-cli settings chat.enableThinking true
kiro-cli settings chat.enableTangentMode true
kiro-cli settings chat.enableTodoList true
kiro-cli settings chat.enableCheckpoint true
kiro-cli settings chat.tangentModeKey "t"
kiro-cli settings chat.delegateModeKey "d"
```

### Knowledge Base Configuration

```bash
kiro-cli settings chat.enableKnowledge true
kiro-cli settings knowledge.defaultIncludePatterns '["*.py", "*.js", "*.md"]'
kiro-cli settings knowledge.defaultExcludePatterns '["*.log", "node_modules", ".git"]'
kiro-cli settings knowledge.maxFiles 2000
```

### Performance Tuning

```bash
kiro-cli settings api.timeout 60                           # Para conexiones lentas
kiro-cli settings knowledge.chunkSize 1024
kiro-cli settings chat.disableAutoCompaction true          # Conservaciones largas
```

---

## Troubleshooting Settings

```bash
# Valores inválidos
kiro-cli settings list --all          # Ver todos los valores válidos

# Resetear un setting
kiro-cli settings --delete <key>

# Verificar archivo de settings
cat ~/.kiro/settings/cli.json

# Editar directamente (solo si sabés lo que hacés)
kiro-cli settings open
```

---

## Environment Variables

| Variable | Descripción |
|---|---|
| `KIRO_LOG_NO_COLOR=1` | Deshabilitar colores en logs |

---

## Settings File

Los settings se almacenan en JSON en `~/.kiro/settings/cli.json`.

> Se recomienda usar `kiro-cli settings` para hacer cambios — proporciona validación automática.