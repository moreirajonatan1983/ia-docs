# Configuration Reference

> **Source:** [kiro.dev/docs/cli/custom-agents/configuration-reference/](https://kiro.dev/docs/cli/custom-agents/configuration-reference/)

---

## Configuration Fields

### `name`
Nombre del agente para identificación y display.
```json
{ "name": "aws-expert" }
```

### `description`
Descripción legible del propósito del agente.
```json
{ "description": "An agent specialized for AWS infrastructure tasks" }
```

### `prompt`
Contexto de alto nivel para el agente (similar a un system prompt). Soporta texto inline o `file://` URIs.
```json
{ "prompt": "You are an expert AWS infrastructure specialist" }
{ "prompt": "file://./prompts/aws-expert.md" }
```
Rutas relativas se resuelven relativas al archivo de configuración del agente.

### `mcpServers`
MCP servers a los que el agente tiene acceso.
```json
{
  "mcpServers": {
    "fetch": { "command": "fetch-server", "args": [] },
    "git": { "command": "git-mcp", "args": [], "timeout": 120000 }
  }
}
```

| Campo | Requerido | Descripción |
|---|---|---|
| `command` | ✅ | Comando para iniciar el servidor |
| `args` | No | Argumentos para el comando |
| `env` | No | Variables de entorno |
| `timeout` | No | Timeout en ms (default: 120000) |

### `tools`
Herramientas disponibles para el agente.
```json
{
  "tools": ["read", "write", "shell", "@git", "@rust-analyzer/check_code"]
}
```

| Sintaxis | Descripción |
|---|---|
| `"read"`, `"shell"` | Herramientas built-in |
| `"@server_name"` | Todas las tools de un MCP server |
| `"@server_name/tool_name"` | Tool específica de un MCP server |
| `"*"` | Todas las tools |
| `"@builtin"` | Todas las tools built-in |

### `toolAliases`
Remapea nombres de tools para resolver conflictos o crear nombres más intuitivos.
```json
{
  "toolAliases": {
    "@github-mcp/get_issues": "github_issues",
    "@gitlab-mcp/get_issues": "gitlab_issues"
  }
}
```

### `allowedTools`
Tools que pueden usarse sin pedir permiso (pre-aprobadas).
```json
{
  "allowedTools": ["read", "@git/git_status", "@server/read_*", "@fetch"]
}
```
Soporta wildcards: `"code_*"`, `"*_bash"`, `"@server/read_*"`.

### `toolsSettings`
Configuración específica para ciertas tools.
```json
{
  "toolsSettings": {
    "write": { "allowedPaths": ["src/**", "tests/**", "Cargo.toml"] },
    "shell": {
      "allowedCommands": ["git status", "git fetch"],
      "deniedCommands": ["git commit .*", "git push .*"],
      "autoAllowReadonly": true
    }
  }
}
```

### `resources`
Recursos locales disponibles para el agente.
```json
{
  "resources": [
    "file://README.md",
    "file://.kiro/steering/**/*.md",
    "skill://.kiro/skills/**/SKILL.md"
  ]
}
```
- `file://` — Se carga en contexto al inicio
- `skill://` — Solo metadatos al inicio, contenido completo bajo demanda

**Knowledge Base:**
```json
{
  "resources": [{
    "type": "knowledgeBase",
    "source": "file://./docs",
    "name": "ProjectDocs",
    "indexType": "best",
    "autoUpdate": true
  }]
}
```

### `hooks`
Comandos que corren en puntos específicos del ciclo de vida del agente.
```json
{
  "hooks": {
    "agentSpawn": [{ "command": "git status" }],
    "userPromptSubmit": [{ "command": "ls -la" }],
    "preToolUse": [{ "matcher": "execute_bash", "command": "echo 'Running bash'" }],
    "postToolUse": [{ "matcher": "fs_write", "command": "cargo fmt --all" }],
    "stop": [{ "command": "npm test" }]
  }
}
```

### `model`
Modelo a usar para este agente. Si no se especifica, usa el modelo por defecto.
```json
{ "model": "claude-sonnet-4" }
```

### `keyboardShortcut`
Atajo de teclado para cambiar rápidamente a este agente.
```json
{ "keyboardShortcut": "ctrl+a" }
```
Formato: `[modifier+]key`. Modificadores: `ctrl`, `shift`. Teclas: `a-z`, `0-9`.

### `welcomeMessage`
Mensaje que se muestra al activar el agente.

---

## File Locations

| Scope | Ubicación | Prioridad |
|---|---|---|
| **Local (workspace)** | `.kiro/agents/<name>.json` | ⬆️ Más alta |
| **Global (user-wide)** | `~/.kiro/agents/<name>.json` | Más baja |

---

## Complete Example

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

## Best Practices

1. **Empezá restrictivo** — Comenzá con acceso mínimo a tools y expandí según sea necesario
2. **Nombres claros** — Usá nombres descriptivos que indiquen el propósito del agente
3. **Documentá el uso** — Agregá descripciones claras para que los miembros del equipo entiendan el agente
4. **Version control** — Almacená configuraciones de agentes en el repositorio del proyecto
5. **Testear a fondo** — Verificá que los permisos de tools funcionen como se espera antes de compartir