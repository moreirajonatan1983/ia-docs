# Referencia de comandos CLI

> **Fuente:** [kiro.dev/docs/cli/reference/cli-commands/](https://kiro.dev/docs/cli/reference/cli-commands/)

---

## Argumentos globales

Estos argumentos funcionan con cualquier comando de Kiro CLI:

| Bandera | Descripción |
|---|---|
| `--verbose` / `-v` / `-vv` / `-vvv` | Nivel de verbosidad de salida |
| `--agente` | Especificar agente a usar |
| `--ayuda` / `-h` | Mostrar ayuda |
| `--versión` / `-V` | Mostrar versión |
| `--ayuda-todos` | Mostrar ayuda extendida |

---

## Comandos

### `kiro-cli chat`

Iniciar una sesión de chat interactivo. `kiro` es un alias de `kiro-cli chat`.

```bash
kiro-cli chat [OPTIONS] [INPUT]
```

| Argumento | Descripción |
|---|---|
| `--no-interactivo` | Modo no interactivo (para guiones/CI) |
| `--resume` / `-r` | Continuar última sesión |
| `--resume-selector` | Selector para elegir sesión y reanudar |
| `--lista-sesiones` | Listar sesiones guardadas |
| `--lista-modelos` | Listar modelos disponibles |
| `--delete-session <ID>` | Eliminar una sesión |
| `--agente <nombre>` | Usar un agente específico |
| `--trust-all-tools` | Pre-aprobar todas las herramientas |
| `--trust-tools <herramienta>` | Herramientas previas a la aprobación específicas |
| `--require-mcp-startup` | Fallar si un servidor MCP no inicia |
| `--envoltura` | Control de ajuste de palabras: `siempre` / `never` / `auto` |
| `ENTRADA` | Prompt directo (sin modo interactivo) |

```bash
kiro-cli                                              # Chat interactivo
kiro-cli chat "How do I list files?"                 # Pregunta directa
kiro-cli chat --no-interactive --trust-all-tools "Show dir"
kiro-cli chat --resume                               # Retomar sesión
kiro-cli chat --list-models --format json
kiro-cli chat --agent my-agent "Help with AWS CLI"
```

---

### `agente kiro-cli`

Gestionar configuraciones de agentes.

```bash
kiro-cli agent [SUBCOMMAND] [AGENT_NAME] [OPTIONS]
```

| Subcomando | Descripción |
|---|---|
| `lista` | Listar agentes disponibles |
| `crear <nombre>` | Crear nuevo agente |
| `editar [nombre]` | Editar agente (actual si no se especifica nombre) |
| `validar` | Validar configuración |
| `migrar` | Migrar a nuevo formato |
| `establecido por defecto` | Definir agente por defecto |

```bash
kiro-cli agent list
kiro-cli agent create my-agent
kiro-cli agent edit my-agent
kiro-cli agent set-default backend-specialist
```

---

### `kiro-cli traducir`

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
| `mcp add --name <n> --command <cmd> --scope <espacio de trabajo\|global>` | Agregar servidor |
| `mcp eliminar --nombre <n> --scope <alcance>` | Eliminar servidor |
| `lista mcp [espacio de trabajo\|global]` | Listar servidores |
| `mcp import --file <archivo> <alcance>` | Importar configuración |
| `estado de mcp --nombre <n>` | Estado de un servidor |

---

### `iniciar sesión en kiro-cli`

Autenticar con Kiro CLI.

```bash
kiro-cli login                                           # Abre browser (local) / device code (SSH)
kiro-cli login --license pro --identity-provider <URL> --region us-east-1
kiro-cli login --social google
kiro-cli login --use-device-flow                         # Forzar device flow
```

---

### `kiro-cli cerrar sesión`

Cerrar sesión. **Termina la sesión en todos los espacios de trabajo** (preserva la configuración y conversaciones guardadas).

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

### `configuración de kiro-cli`

Gestionar la configuración del CLI.

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

Diagnosticar y solucionar problemas comunes de instalación.

```bash
kiro-cli doctor
kiro-cli doctor --all      # Todos los checks
kiro-cli doctor --strict   # Modo estricto (falla en warnings)
```

---

### `actualización de kiro-cli`

Actualiza Kiro CLI a la última versión.

```bash
kiro-cli update
kiro-cli update --non-interactive    # Sin commit
```

---

### `tema kiro-cli`

Cambiar tema visual del menú de autocompletado.

```bash
kiro-cli theme --list
kiro-cli theme dark
kiro-cli theme light
kiro-cli theme system
```

---

### `integraciones kiro-cli`

Gestionar integraciones del sistema.

```bash
kiro-cli integrations install kiro-command-router   # Instalar kiro command router (v1.26+)
kiro-cli integrations status
kiro-cli integrations uninstall --silent
```

**Kiro Command Router (v1.26+):** permite que `kiro` lance CLI o IDE según tu preferencia.
```golpecito
kiro configurado por defecto cli # kiro → CLI
kiro set-default ide # kiro → IDE
```

---

### `kiro-cli en línea`

Gestionar sugerencias en línea (texto fantasma).

```bash
kiro-cli inline enable
kiro-cli inline disable
kiro-cli inline status
```

---

### `diagnóstico kiro-cli`

Generar informe de diagnóstico del sistema.

```bash
kiro-cli diagnostic
kiro-cli diagnostic --format json-pretty
kiro-cli diagnostic --force    # Sin requerir que la app esté corriendo
```

---

### `problema de kiro-cli`

Cree un problema en GitHub para errores o comentarios.

```bash
kiro-cli issue
kiro-cli issue "Autocomplete not working in zsh"
```

---

### `versión kiro-cli`

Mostrar versión e información del registro de cambios.

```bash
kiro-cli version
kiro-cli version --changelog
kiro-cli version --changelog=all
kiro-cli version --changelog=1.5.0
```

---

## Gestión de sesiones

```golpecito
# Desde la terminal
kiro-cli chat --list-sessions # Listar sesiones
kiro-cli chat --resume # Retomar última sesión
kiro-cli chat --resume-picker # Picker interactivo de sesiones
kiro-cli chat --delete-session <ID> # Eliminar sesión

# Almacenamiento personalizado
# Por defecto: ~/.kiro/chat-history/
```

---

## Archivos de registro

Los registros se almacenan en `~/.kiro/logs/`. Uso de para depuración:
```golpecito
kiro-cli --verbose chat "..." # -v, -vv, -vvv para más detalles
```