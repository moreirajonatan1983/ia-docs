# Slash Commands Reference

> **Source:** [kiro.dev/docs/cli/reference/slash-commands/](https://kiro.dev/docs/cli/reference/slash-commands/)

---

## Overview

Los slash commands son comandos especiales disponibles dentro de una sesión de chat interactiva. Empiezan con `/` y proveen shortcuts para tareas comunes.

Solo disponibles en **modo interactivo**: `kiro chat > /comando`

---

## Quick Reference

| Comando | Descripción |
|---|---|
| `/help` | Cambiar al Help Agent o mostrar ayuda |
| `/quit` | Salir de la sesión (alias: `/exit`, `/q`) |
| `/clear` | Limpiar historia de conversación en pantalla |
| `/context` | Gestionar archivos de contexto |
| `/model` | Seleccionar modelo de AI |
| `/agent` | Gestionar y cambiar entre agentes |
| `/chat` | Gestionar sesiones de chat |
| `/save` | Guardar la conversación |
| `/load` | Cargar una conversación guardada |
| `/editor` | Abrir editor externo para el prompt |
| `/reply` | Responder al último mensaje |
| `/checkpoint` | Crear/gestionar checkpoints |
| `/plan` | Activar el Plan Agent |
| `/knowledge` | Gestionar knowledge base (experimental) |
| `/compact` | Compactar el historial de conversación |
| `/paste` | Pegar contenido del clipboard |
| `/tools` | Ver y gestionar permisos de tools |
| `/prompts` | Ver y gestionar prompts |
| `/hooks` | Ver context hooks activos |
| `/usage` | Ver billing y créditos |
| `/mcp` | Ver servidores MCP cargados |
| `/code` | Gestionar code intelligence (LSP) |
| `/experiment` | Toggle features experimentales |
| `/tangent` | Crear checkpoint de conversación |
| `/todos` | Ver y gestionar TODO lists |
| `/issue` | Crear un GitHub issue |
| `/logdump` | Crear zip con logs para soporte |
| `/changelog` | Ver changelog del CLI |

---

## Commands Detail

### `/help`

```
> /help                           # Cambiar al Help Agent
> /help How do I configure MCP?   # Pregunta directa al Help Agent
> /help --legacy                  # Texto de ayuda clásico
```

### `/context`

```
> /context show                   # Ver configuración y archivos de contexto
> /context add src/app.js
> /context add "*.py"
> /context add "src/**/*.js"
> /context remove src/app.js
> /context clear
```
> Los cambios NO se preservan entre sesiones. Para hacerlos permanentes, editar el archivo de configuración del agente.

### `/model`

```
> /model                              # Picker interactivo
> /model claude-opus-4.6              # Selección directa
> /model set-current-as-default       # Guardar como default
```
Soporta tab-completion y fuzzy matching.

### `/agent`

```
> /agent list
> /agent create my-agent
> /agent create my-agent -D "Code reviewer" -m code-analysis
> /agent create my-agent --manual
> /agent edit                         # Editar agente actual
> /agent edit my-agent
> /agent schema                       # Ver schema de configuración
> /agent set-default my-agent
> /agent swap code-reviewer
```

### `/tools`

```
> /tools                    # Ver todas las tools y permisos
> /tools schema             # Ver input schema de todas las tools
> /tools trust write        # Trust específica para esta sesión
> /tools untrust write      # Volver a solicitar confirmación
> /tools trust-all          # Trust todas (usar con precaución)
> /tools reset              # Resetear a niveles por defecto
```

Output columns: `~Tokens`, `Permission` (Trusted / Ask / Allowed), `Total`.

### `/prompts`

```
> /prompts list
> /prompts details code-review
> /prompts get code-review [arg]
> @code-review [arg]              # Shortcut directo
> /prompts create my-prompt
> /prompts edit my-prompt
> /prompts remove my-prompt
```

### `/code`

```
> /code init             # Inicializar LSP para code intelligence
> /code init -f          # Forzar reinicialización
> /code overview         # Overview del workspace
> /code status           # Estado de LSP servers
> /code logs             # Ver logs LSP
> /code logs -l INFO -n 50
> /code logs -p ./lsp-logs.json
```

### `/checkpoint` (experimental)

```
> /checkpoint list
> /checkpoint expand <tag>
> /checkpoint diff <tag1> [tag2]
> /checkpoint restore [<tag>]
> /checkpoint clean
```

### `/logdump`

```
> /logdump          # Crear zip con chat logs
> /logdump --mcp    # Incluir MCP logs
```
Crea: `q-logs-YYYY-MM-DDTHH-MM-SSZ.zip`

### `/todos` (experimental)

```
> /todo
> /todo add "Fix authentication bug"
> /todo complete 1
```

---

## Keyboard Shortcuts (Interactive Mode)

| Atajo | Acción |
|---|---|
| `Ctrl+C` | Cancelar input actual |
| `Ctrl+J` | Insertar nueva línea (multi-line prompt) |
| `Ctrl+S` | Fuzzy search de comandos y archivos de contexto |
| `Ctrl+T` | Toggle tangent mode |
| `↑` / `↓` | Navegar historial de comandos |