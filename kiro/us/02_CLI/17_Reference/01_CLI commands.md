# CLI Commands Reference

> **Source:** [kiro.dev/docs/cli/reference/cli-commands/](https://kiro.dev/docs/cli/reference/cli-commands/)

---

## Global Arguments

Estos argumentos funcionan con cualquier comando de Kiro CLI:

| Flag | Descripción |
|---|---|
| `--verbose` / `-v` / `-vv` / `-vvv` | Nivel de verbosidad de output |
| `--agent` | Especificar agente a usar |
| `--help` / `-h` | Mostrar ayuda |
| `--version` / `-V` | Mostrar versión |
| `--help-all` | Mostrar ayuda extendida |

---

## Commands

### `kiro-cli chat`

Iniciar una sesión de chat interactivo. `kiro` es un alias de `kiro-cli chat`.

```bash
kiro-cli chat [OPTIONS] [INPUT]
```

| Argumento | Descripción |
|---|---|
| `--no-interactive` | Modo no interactivo (para scripts/CI) |
| `--resume` / `-r` | Continuar última sesión |
| `--resume-picker` | Picker para elegir sesión a resumir |
| `--list-sessions` | Listar sesiones guardadas |
| `--list-models` | Listar modelos disponibles |
| `--delete-session <ID>` | Eliminar una sesión |
| `--agent <name>` | Usar un agente específico |
| `--trust-all-tools` | Pre-aprobar todas las tools |
| `--trust-tools <tool>` | Pre-aprobar tools específicas |
| `--require-mcp-startup` | Fallar si un MCP server no inicia |
| `--wrap` | Control de word wrap: `always` / `never` / `auto` |
| `INPUT` | Prompt directo (sin modo interactivo) |

```bash
kiro-cli                                              # Chat interactivo
kiro-cli chat "How do I list files?"                 # Pregunta directa
kiro-cli chat --no-interactive --trust-all-tools "Show dir"
kiro-cli chat --resume                               # Retomar sesión
kiro-cli chat --list-models --format json
kiro-cli chat --agent my-agent "Help with AWS CLI"
```

---

### `kiro-cli agent`

Gestionar configuraciones de agentes.

```bash
kiro-cli agent [SUBCOMMAND] [AGENT_NAME] [OPTIONS]
```

| Subcomando | Descripción |
|---|---|
| `list` | Listar agentes disponibles |
| `create <name>` | Crear nuevo agente |
| `edit [name]` | Editar agente (actual si no se especifica nombre) |
| `validate` | Validar configuración |
| `migrate` | Migrar a nuevo formato |
| `set-default` | Definir agente por defecto |

```bash
kiro-cli agent list
kiro-cli agent create my-agent
kiro-cli agent edit my-agent
kiro-cli agent set-default backend-specialist
```

---

### `kiro-cli translate`

Traducir instrucciones en lenguaje natural a comandos shell ejecutables.

```bash
kiro-cli translate "list all Python files modified last week"
kiro-cli translate -n 3 "search for text in files"   # Mostrar 3 opciones
```

---

### `kiro-cli mcp`

Gestionar servidores MCP.

| Subcomando | Descripción |
|---|---|
| `mcp add --name <n> --command <cmd> --scope <workspace\|global>` | Agregar servidor |
| `mcp remove --name <n> --scope <scope>` | Eliminar servidor |
| `mcp list [workspace\|global]` | Listar servidores |
| `mcp import --file <file> <scope>` | Importar configuración |
| `mcp status --name <n>` | Estado de un servidor |

---

### `kiro-cli login`

Autenticar con Kiro CLI.

```bash
kiro-cli login                                           # Abre browser (local) / device code (SSH)
kiro-cli login --license pro --identity-provider <URL> --region us-east-1
kiro-cli login --social google
kiro-cli login --use-device-flow                         # Forzar device flow
```

---

### `kiro-cli logout`

Cerrar sesión. **Termina la sesión en todos los workspaces** (preserva configuraciones y conversaciones guardadas).

```bash
kiro-cli logout
```

---

### `kiro-cli whoami`

Ver información del usuario autenticado.

```bash
kiro-cli whoami
kiro-cli whoami --format json-pretty
```

---

### `kiro-cli settings`

Gestionar configuración del CLI.

```bash
kiro-cli settings list                          # Ver todos los settings
kiro-cli settings list --all                    # Ver todos los settings disponibles
kiro-cli settings telemetry.enabled             # Ver un setting
kiro-cli settings telemetry.enabled false       # Setear un setting
kiro-cli settings --delete chat.defaultModel    # Eliminar un setting
kiro-cli settings open                          # Abrir archivo de settings en editor
kiro-cli settings list --format json-pretty
```

---

### `kiro-cli doctor`

Diagnosticar y arreglar problemas comunes de instalación.

```bash
kiro-cli doctor
kiro-cli doctor --all      # Todos los checks
kiro-cli doctor --strict   # Modo estricto (falla en warnings)
```

---

### `kiro-cli update`

Actualizar Kiro CLI a la última versión.

```bash
kiro-cli update
kiro-cli update --non-interactive    # Sin confirmación
```

---

### `kiro-cli theme`

Cambiar tema visual del menú de autocompletado.

```bash
kiro-cli theme --list
kiro-cli theme dark
kiro-cli theme light
kiro-cli theme system
```

---

### `kiro-cli integrations`

Gestionar integraciones del sistema.

```bash
kiro-cli integrations install kiro-command-router   # Instalar kiro command router (v1.26+)
kiro-cli integrations status
kiro-cli integrations uninstall --silent
```

**Kiro Command Router (v1.26+):** permite que `kiro` lance CLI o IDE según tu preferencia.
```bash
kiro set-default cli   # kiro → CLI
kiro set-default ide   # kiro → IDE
```

---

### `kiro-cli inline`

Gestionar sugerencias inline (ghost text).

```bash
kiro-cli inline enable
kiro-cli inline disable
kiro-cli inline status
```

---

### `kiro-cli diagnostic`

Generar reporte de diagnóstico del sistema.

```bash
kiro-cli diagnostic
kiro-cli diagnostic --format json-pretty
kiro-cli diagnostic --force    # Sin requerir que la app esté corriendo
```

---

### `kiro-cli issue`

Crear un issue en GitHub para bugs o feedback.

```bash
kiro-cli issue
kiro-cli issue "Autocomplete not working in zsh"
```

---

### `kiro-cli version`

Mostrar versión e información del changelog.

```bash
kiro-cli version
kiro-cli version --changelog
kiro-cli version --changelog=all
kiro-cli version --changelog=1.5.0
```

---

## Session Management

```bash
# Desde el terminal
kiro-cli chat --list-sessions          # Listar sesiones
kiro-cli chat --resume                 # Retomar última sesión
kiro-cli chat --resume-picker          # Picker interactivo de sesiones
kiro-cli chat --delete-session <ID>    # Eliminar sesión

# Almacenamiento personalizado
# Por defecto: ~/.kiro/chat-history/
```

---

## Log Files

Los logs se almacenan en `~/.kiro/logs/`. Para debugging use:
```bash
kiro-cli --verbose chat "..."      # -v, -vv, -vvv para más detalle
```