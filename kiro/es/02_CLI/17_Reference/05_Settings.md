# Referencia de configuración

> **Fuente:** [kiro.dev/docs/cli/reference/settings/](https://kiro.dev/docs/cli/reference/settings/)

---

## Accediendo a la configuración

```bash
kiro-cli settings list                          # Settings actuales
kiro-cli settings list --all                    # Todos los disponibles
kiro-cli settings <key>                         # Ver valor de un setting
kiro-cli settings <key> <value>                 # Setear un setting
kiro-cli settings --delete <key>                # Eliminar un setting
kiro-cli settings open                          # Abrir archivo en editor
kiro-cli settings list --format json-pretty     # Output JSON
```

**Archivo de configuración:** `~/.kiro/settings/cli.json`

---

## Referencia de configuración

### Telemetría y Privacidad

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `telemetría.habilitada` | `verdadero` | Habilitar/deshabilitar telemetría |
| `telemetríaClientId` | `"cliente-123"` | ID de cliente para telemetría |

```bash
kiro-cli settings telemetry.enabled false    # Deshabilitar telemetría
```

---

### Interfaz de chat

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `chat.defaultModel` | `"claude-3-soneto"` | Modelo por defecto |
| `chat.defaultAgent` | `"mi-agente"` | Agente por defecto |
| `chat.diffTool` | `"delta"` | Herramienta diferencial externa |
| `chat.saludo.habilitado` | `falso` | Mostrar/ocultar saludo inicial |
| `chat.editMode` | `verdadero` | Modo edición en línea |
| `chat.enableNotificaciones` | `verdadero` | Notificaciones del sistema |
| `chat.disableMarkdownRendering` | `falso` | Deshabilitar render de Markdown |
| `chat.disableAutoCompaction` | `verdadero` | Deshabilitar compactación automática |
| `compactación.excludeMessages` | `2` | Mensajes a eliminar de compactación |
| `compactation.excludeContextWindowPercent` | `2` | % de ventana de contexto a eliminar |
| `chat.enablePromptHints` | `falso` | Mostrar sugerencias de indicaciones |
| `chat.enableHistoryHints` | `verdadero` | Mostrar pistas del historial |
| `chat.uiMode` | `"compacto"` | Modo UI (`compacto` / `predeterminado`) |
| `chat.enableContextUsageIndicator` | `verdadero` | Indicador de uso de contexto |

---

### Base de conocimientos (experimental)

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `chat.enableKnowledge` | `verdadero` | Habilitar base de conocimientos |
| `knowledge.defaultIncludePatterns` | `'["*.py", "*.js"]'` | Patrones de archivos a incluir |
| `knowledge.defaultExcludePatterns` | `'["*.log", "node_modules"]'` | Patrones a eliminar |
| `conocimiento.maxFiles` | `1000` | Máximo de archivos a indexar |
| `conocimiento.chunkSize` | `512` | Tamaño de trozo para indexado |
| `conocimiento.chunkOverlap` | `50` | Superposición entre trozos |
| `conocimiento.tipo de índice` | `"rápido"` | Tipo de índice: `"mejor"` / `"rápido"` |

---

### Atajos de teclas

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `chat.skimCommandKey` | `"f"` | Tecla para modo skim |
| `chat.autocompletionKey` | `"Pestaña"` | Tecla de autocompletado |
| `chat.tangentModeKey` | `"t"` | Tecla para modo tangente |
| `chat.delegateModeKey` | `"d"` | Tecla para modo delegar |

---

### Alternancia de funciones (experimental)

| Configuración | comando | Descripción |
|---|---|---|
| `chat.enableThinking` | `kiro-cli configuración chat.enableThinking true` | Herramienta de pensamiento |
| `chat.enableTangentMode` | `kiro-cli configuración chat.enableTangentMode true` | Modo tangente |
| `chat.enableTodoList` | `kiro-cli configuración chat.enableTodoList verdadero` | Listas de tareas pendientes |
| `chat.enableCheckpoint` | `configuración de kiro-cli chat.enableCheckpoint verdadero` | Puntos de control |
| `chat.enableDelegate` | `kiro-cli configuración chat.enableDelegate true` | Delegar tareas |
| `introspect.tangentMode` | `Configuración de kiro-cli introspect.tangentMode true` | Tangente en introspección |

---

### API y servicio

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `api.tiempo de espera` | `30` | Timeout en segundos para solicitudes a la API |

---

### Protocolo de contexto modelo (MCP)

| Configuración | Ejemplo | Descripción |
|---|---|---|
| `mcp.initTimeout` | `10` | Timeout de inicialización del servidor MCP |
| `mcp.noInteractiveTimeout` | `5` | Timeout en modo no interactivo |
| `mcp.loadedBefore` | `verdadero` | Bandera de inicialización previa |

---

## Ejemplos de configuración comunes

### Configuración básica

```bash
kiro-cli settings telemetry.enabled false
kiro-cli settings chat.defaultModel "claude-3-sonnet"
kiro-cli settings chat.greeting.enabled false
```

### Habilitar funciones experimentales

```bash
kiro-cli settings chat.enableThinking true
kiro-cli settings chat.enableTangentMode true
kiro-cli settings chat.enableTodoList true
kiro-cli settings chat.enableCheckpoint true
kiro-cli settings chat.tangentModeKey "t"
kiro-cli settings chat.delegateModeKey "d"
```

### Configuración de la base de conocimientos

```bash
kiro-cli settings chat.enableKnowledge true
kiro-cli settings knowledge.defaultIncludePatterns '["*.py", "*.js", "*.md"]'
kiro-cli settings knowledge.defaultExcludePatterns '["*.log", "node_modules", ".git"]'
kiro-cli settings knowledge.maxFiles 2000
```

### Ajuste de rendimiento

```bash
kiro-cli settings api.timeout 60                           # Para conexiones lentas
kiro-cli settings knowledge.chunkSize 1024
kiro-cli settings chat.disableAutoCompaction true          # Conservaciones largas
```

---

## Configuración de solución de problemas

```golpecito
# Valores inválidos
lista de configuraciones de kiro-cli --all # Ver todos los valores válidos

# Restablecer una configuración
configuración de kiro-cli --eliminar <clave>

# Verificar archivo de configuración
gato ~/.kiro/settings/cli.json

# Editar directamente (solo si sabés lo que haces)
configuración de kiro-cli abierta
```

---

## Variables de entorno

| Variables | Descripción |
|---|---|
| `KIRO_LOG_NO_COLOR=1` | Deshabilitar colores en registros |

---

## Archivo de configuración

Los Settings se almacenan en JSON en `~/.kiro/settings/cli.json`.

> Se recomienda usar `kiro-cli settings` para hacer cambios — proporciona validación automática.