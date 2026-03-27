# Built-in Tools

> **Source:** [kiro.dev/docs/cli/reference/built-in-tools/](https://kiro.dev/docs/cli/reference/built-in-tools/)

---

## Overview

Las built-in tools son las capacidades nativas que Kiro CLI puede usar para interactuar con el sistema de archivos, ejecutar comandos, buscar en la web, y más.

---

## File Read

Lee el contenido de archivos locales.

**Opciones de configuración:**
```json
{
  "toolsSettings": {
    "read": {
      "allowedPaths": ["src/**", "docs/**"],
      "deniedPaths": [".env", "**/*.key"]
    }
  }
}
```

---

## Glob

Busca archivos usando patrones glob.

**Opciones de configuración:**
```json
{
  "toolsSettings": {
    "glob": {
      "allowedPaths": ["./src/**"]
    }
  }
}
```

Ejemplo de uso: `Find all TypeScript files in the src directory`

---

## Grep

Busca texto en archivos usando expresiones regulares.

**Opciones de configuración:**
```json
{
  "toolsSettings": {
    "grep": {
      "allowedPaths": ["./src/**"],
      "maxResults": 100
    }
  }
}
```

---

## File Write

Escribe o modifica archivos locales.

**Custom diff tools:** Podés configurar herramientas externas como `delta`, `difftastic`, etc. Ver [Custom diff tools →](../03_Chat/14_Custom diff tools.md).

**Opciones de configuración:**
```json
{
  "toolsSettings": {
    "write": {
      "allowedPaths": ["src/**", "tests/**", "Cargo.toml"],
      "deniedPaths": [".env", "**/*.lock"]
    }
  }
}
```

---

## Execute Shell Commands

Ejecuta comandos shell en el sistema.

**Opciones de configuración:**
```json
{
  "toolsSettings": {
    "shell": {
      "allowedCommands": ["git status", "npm test", "cargo build"],
      "deniedCommands": ["rm -rf .*", "sudo .*"],
      "autoAllowReadonly": true
    }
  }
}
```

> `autoAllowReadonly: true` — pre-aprueba automáticamente comandos de solo lectura.

---

## Execute AWS Commands

Permite ejecutar comandos de AWS CLI directamente. Requiere que `aws-cli` esté instalado y configurado.

```
"Run aws s3 ls to list my buckets"
"Check the status of my CloudFormation stack"
```

---

## Web Search and Fetch

### web_search
Busca información en la web.

### web_fetch
Obtiene contenido de URLs específicas.

**Fetch modes:**
| Modo | Descripción |
|---|---|
| `auto` | Kiro elige el mejor modo |
| `raw` | HTML sin procesar |
| `text` | Texto plano extraído |
| `markdown` | Convertido a Markdown |

**Configuración:**
```json
{
  "toolsSettings": {
    "web_search": { "enabled": true },
    "web_fetch": { "enabled": true }
  }
}
```

**Limitaciones:**
- No puede acceder a páginas que requieren autenticación
- Algunas páginas pueden bloquear el acceso programático
- Rate limits pueden aplicar

---

## Introspect Kiro CLI Capabilities

Tool que permite a Kiro responder preguntas sobre sus propias capacidades, configuración y estado.

**Preguntas de ejemplo:**
- "¿Cuáles son los comandos disponibles?"
- "¿Cómo configuro un MCP server?"
- "¿Qué agent estoy usando actualmente?"

---

## Code Intelligence

Integración con Language Server Protocol (LSP) para análisis de código avanzado:
- Hover information
- Go to definition
- Find references
- Diagnostics de código

Inicializar con `/code init` en el chat.

---

## Delegate Tasks (Experimental)

Permite lanzar tareas asíncronas en background. Ver [Delegate →](../09_Experimental/06_Delegate.md).

---

## Submit Issue / Feature Request

Tool para crear issues en GitHub directamente desde el chat. También disponible como `/issue`.

---

## Knowledge Tool (Experimental)

Acceso a la knowledge base para búsqueda semántica persistente. Ver [Knowledge Management →](../09_Experimental/01_Knowledge management.md).

---

## Thinking Tool (Experimental)

Muestra el proceso de razonamiento de la IA paso a paso. Ver [Thinking Tool →](../09_Experimental/04_Thinking tool.md).

---

## ToDo List Tool (Experimental)

Gestión de listas de tareas persistentes. Ver [TODO Lists →](../09_Experimental/03_TODO lists.md).

---

## Tool Permissions

Por defecto, Kiro solicita confirmación para tools que pueden modificar el sistema:

| Tool | Permiso por defecto |
|---|---|
| `read` | Auto-aprobado |
| `glob` | Auto-aprobado |
| `grep` | Auto-aprobado |
| `write` | Requiere confirmación |
| `shell` | Requiere confirmación |
| `aws` | Requiere confirmación |
| `web_search` | Auto-aprobado |
| `web_fetch` | Auto-aprobado |

Gestioná permisos con `/tools trust`, `/tools untrust`, `/tools trust-all`.

---

## Using Tool Settings in Agent Configuration

```json
{
  "toolsSettings": {
    "write": { "allowedPaths": ["src/**"] },
    "shell": {
      "allowedCommands": ["git status", "npm test"],
      "autoAllowReadonly": true
    },
    "@custom-mcp/my_tool": {
      "custom_param": "value"
    }
  }
}
```