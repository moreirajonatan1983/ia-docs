# Referencia de comandos de barra diagonal

> **Fuente:** [kiro.dev/docs/cli/reference/slash-commands/](https://kiro.dev/docs/cli/reference/slash-commands/)

---

## Descripción general

Los comandos de barra diagonal son comandos especiales disponibles dentro de una sesión de chat interactiva. Empiezan con `/` y proporcionan atajos para tareas comunes.

Solo disponibles en **modo interactivo**: `kiro chat > ​​/comando`

---

## Referencia rápida

| comando | Descripción |
|---|---|
| `/ayuda` | Cambiar al Agente de Ayuda o mostrar ayuda |
| `/salir` | Salir de la sesión (alias: `/exit`, `/q`) |
| `/claro` | Limpiar historia de conversación en pantalla |
| `/ contexto` | Gestionar archivos de contexto |
| `/modelo` | Seleccionar modelo de AI |
| `/agente` | Gestionar y cambiar entre agentes |
| `/chat` | Gestionar sesiones de chat |
| `/guardar` | Guardar la conversación |
| `/cargar` | Cargar una conversación guardada |
| `/editor` | Abrir editor externo para el indicador |
| `/responder` | Responder al último mensaje |
| `/punto de control` | Crear/gestionar puntos de control |
| `/plan` | Activar el Plan Agente |
| `/conocimiento` | Gestionar base de conocimientos (experimental) |
| `/ compacto` | Compactar el historial de conversación |
| `/pegar` | Pegar contenido del portapapeles |
| `/herramientas` | Ver y gestionar permisos de herramientas |
| `/solicitudes` | Ver y gestionar avisos |
| `/hooks` | Ver contexto engancha activos |
| `/ uso` | Ver facturación y créditos |
| `/mcp` | Ver servidores MCP cargados |
| `/código` | Gestionar inteligencia de código (LSP) |
| `/experimento` | Alternar funciones experimentales |
| `/ tangente` | Crear punto de control de conversación |
| `/todos` | Ver y gestionar listas TODO |
| `/ problema` | Crear un problema de GitHub |
| `/logdump` | Crear zip con registros para soporte |
| `/ registro de cambios` | Ver registro de cambios del CLI |

---

## Detalle de comandos

### `/ayuda`

```
> /help                           # Cambiar al Help Agent
> /help How do I configure MCP?   # Pregunta directa al Help Agent
> /help --legacy                  # Texto de ayuda clásico
```

### `/ contexto`

```
> /context show # Ver configuración y archivos de contexto
> /context agregar src/app.js
> /context agregar "*.py"
> /context agregar "src/**/*.js"
> /context eliminar src/app.js
> /contexto claro
```
> Los cambios NO se conservan entre sesiones. Para hacerlo permanentemente, edite el archivo de configuración del agente.

### `/modelo`

```
> /modelo # Picker interactivo
> /model claude-opus-4.6 # Selección directa
> /model set-current-as-default # Guardar como predeterminado
```
Soporta tabulación y coincidencia difusa.

### `/agente`

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

### `/herramientas`

```
> /tools                    # Ver todas las tools y permisos
> /tools schema             # Ver input schema de todas las tools
> /tools trust write        # Trust específica para esta sesión
> /tools untrust write      # Volver a solicitar commit
> /tools trust-all          # Trust todas (usar con precaución)
> /tools reset              # Resetear a niveles por defecto
```

Columnas de salida: `~Tokens`, `Permiso` (Confiable/Preguntar/Permitido), `Total`.

### `/solicitudes`

```
> /prompts list
> /prompts details code-review
> /prompts get code-review [arg]
> @code-review [arg]              # Shortcut directo
> /prompts create my-prompt
> /prompts edit my-prompt
> /prompts remove my-prompt
```

### `/código`

```
> /code init             # Inicializar LSP para code intelligence
> /code init -f          # Forzar reinicialización
> /code overview         # Overview del workspace
> /code status           # Estado de LSP servers
> /code logs             # Ver logs LSP
> /code logs -l INFO -n 50
> /code logs -p ./lsp-logs.json
```

### `/punto de control` (experimental)

```
> /checkpoint list
> /checkpoint expand <tag>
> /checkpoint diff <tag1> [tag2]
> /checkpoint restore [<tag>]
> /checkpoint clean
```

### `/logdump`

```
> /logdump # Crear registros de chat zip con
> /logdump --mcp # Incluir registros de MCP
```
Crea: `q-logs-AAAA-MM-DDTHH-MM-SSZ.zip`

### `/todos` (experimental)

```
> /todo
> /todo add "Fix authentication bug"
> /todo complete 1
```

---

## Atajos de teclado (modo interactivo)

| Atajó | Acción |
|---|---|
| `Ctrl+C` | Cancelar entrada real |
| `Ctrl+J` | Insertar nueva línea (mensaje multilínea) |
| `Ctrl+S` | Búsqueda difusa de comandos y archivos de contexto |
| `Ctrl+T` | Alternar modo tangente |
| ` ↑` / `↓` | Navegar historial de comandos |