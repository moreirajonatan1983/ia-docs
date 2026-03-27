# Referencia de configuración

> **Fuente:** [kiro.dev/docs/cli/custom-agents/configuration-reference/](https://kiro.dev/docs/cli/custom-agents/configuration-reference/)

---

## Campos de configuración

### `nombre`
Nombre del agente para identificación y visualización.
```json
{ "nombre": "aws-experto" }
```

### `descripción`
Descripción legible del propósito del agente.
```json
{ "description": "Un agente especializado en tareas de infraestructura de AWS" }
```

### `aviso`
Contexto de alto nivel para el agente (similar a un aviso del sistema). Soporta texto en línea en `file://` URI.
```json
{ "prompt": "Usted es un experto especialista en infraestructura de AWS" }
{ "prompt": "archivo://./prompts/aws-expert.md" }
```
Rutas relativas se resuelven relativas al archivo de configuración del agente.

### `mcpServidores`
Servidores MCP a los que el agente tiene acceso.
```json
{
  "mcpServers": {
    "fetch": { "comando": "fetch-server", "args": [] },
    "git": { "comando": "git-mcp", "args": [], "timeout": 120000 }
  }
}
```

| Campo | Requerido | Descripción |
|---|---|---|
| `comando` | ✅ | Comando para iniciar el servidor |
| `argumentos` | No | Argumentos para el comando |
| `entorno` | No | Variables de entorno |
| `tiempo de espera` | No | Tiempo de espera en ms (predeterminado: 120000) |

### `herramientas`
Herramientas disponibles para el agente.
```json
{
  "herramientas": ["leer", "escribir", "shell", "@git", "@rust-analyzer/check_code"]
}
```

| Sintaxis | Descripción |
|---|---|
| `"leer"`, `"shell"` | Herramientas incorporadas |
| `"@nombre_servidor"` | Todas las herramientas de un servidor MCP |
| `"@nombre_servidor/nombre_herramienta"` | Herramienta específica de un servidor MCP |
| `"*"` | Todas las herramientas |
| `"@integrado"` | Todas las herramientas integradas |

### `aliases de herramienta`
Remapea nombres de herramientas para resolver conflictos o crear nombres más intuitivos.
```json
{
  "alias de herramienta": {
    "@github-mcp/get_issues": "github_issues",
    "@gitlab-mcp/get_issues": "gitlab_issues"
  }
}
```

### `herramientas permitidas`
Herramientas que pueden usarse sin pedir permiso (preaprobadas).
```json
{
  "allowedTools": ["leer", "@git/git_status", "@server/read_*", "@fetch"]
}
```
Soporta comodines: `"code_*"`, `"*_bash"`, `"@server/read_*"`.

### `herramientasConfiguración`
Configuración específica para ciertas herramientas.
```json
{
  "Configuración de herramientas": {
    "escribir": { "allowedPaths": ["src/**", "pruebas/**", "Cargo.toml"] },
    "cáscara": {
      "allowedCommands": ["git status", "git fetch"],
      "deniedCommands": ["git commit.*", "git push.*"],
      "autoAllowReadonly": verdadero
    }
  }
}
```

### `recursos`
Recursos locales disponibles para el agente.
```json
{
  "recursos": [
    "archivo://README.md",
    "archivo://.kiro/steering/**/*.md",
    "habilidad://.kiro/skills/**/SKILL.md"
  ]
}
```
- `file://` — Se carga en contexto al inicio
- `skill://` — Solo metadatos al inicio, contenido completo bajo demanda

**Base de conocimientos:**
```json
{
  "recursos": [{
    "tipo": "base de conocimientos",
    "fuente": "archivo://./docs",
    "nombre": "Documentos del proyecto",
    "indexType": "mejor",
    "actualización automática": verdadero
  }]
}
```

### `hooks`
Comandos que corren en puntos específicos del ciclo de vida del agente.
```json
{
  "hooks": {
    "agentSpawn": [{ "comando": "estado de git" }],
    "userPromptSubmit": [{ "command": "ls -la" }],
    "preToolUse": [{ "matcher": "execute_bash", "command": "echo 'Running bash'" }],
    "postToolUse": [{ "matcher": "fs_write", "command": "cargo fmt --all" }],
    "detener": [{ "comando": "prueba npm" }]
  }
}
```

### `modelo`
Modelo a usar para este agente. Si no se especifica, usa el modelo por defecto.
```json
{ "modelo": "claude-sonnet-4" }
```

### `atajo de teclado`
Atajo de teclado para cambiar rápidamente a este agente.
```json
{ "tecladoAtajo": "ctrl+a" }
```
Formato: `[modificador+]clave`. Modificadores: `ctrl`, `shift`. Teclas: `a-z`, `0-9`.

### `mensaje de bienvenida`
Mensaje que se muestra al activar el agente.

---

## Ubicaciones de archivos

| Alcance | Ubicación | Prioridad |
|---|---|---|
| **Local (espacio de trabajo)** | `.kiro/agents/<nombre>.json` | ⬆️Más alta |
| **Global (todo el usuario)** | `~/.kiro/agents/<nombre>.json` | Más baja |

---

## Ejemplo completo

```json
{
  "name": "aws-rust-agent",
  "description": "Specialized agent for AWS and Rust development",
  "prompt": "file://./prompts/aws-rust-expert.md",
  "mcpServers": {
    "fetch": { "command": "fetch-server", "args": [] },
    "git": { "command": "git-mcp", "args": [] }
  },
  "tools": ["read", "write", "shell", "aws", "@git", "@fetch/fetch_url"],
  "toolAliases": {
    "@git/git_status": "status",
    "@fetch/fetch_url": "get"
  },
  "allowedTools": ["read", "@git/git_status"],
  "toolsSettings": {
    "write": { "allowedPaths": ["src/**", "tests/**", "Cargo.toml"] },
    "aws": { "allowedServices": ["s3", "lambda"], "autoAllowReadonly": true }
  },
  "resources": ["file://README.md", "file://docs/**/*.md"],
  "hooks": {
    "agentSpawn": [{ "command": "git status" }],
    "postToolUse": [{ "matcher": "fs_write", "command": "cargo fmt --all" }]
  },
  "model": "claude-sonnet-4",
  "keyboardShortcut": "ctrl+shift+r",
  "welcomeMessage": "Ready to help with AWS and Rust development!"
}
```

---

## Mejores prácticas

1. **Empezá restrictivo** — Comenzá con acceso mínimo a herramientas y expandí según sea necesario
2. **Nombres claros** — Usá nombres descriptivos que indican el propósito del agente
3. **Documentá el uso** — Agrega descripciones claras para que los miembros del equipo entiendan el agente
4. **Control de versiones** — Almacená configuraciones de agentes en el repositorio del proyecto
5. **Tesear a fondo** — Verifica que los permisos de herramientas funcionen como se espera antes de compartir