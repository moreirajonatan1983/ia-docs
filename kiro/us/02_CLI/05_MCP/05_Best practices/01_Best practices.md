# MCP Best Practices

> **Source:** [kiro.dev/docs/cli/mcp/](https://kiro.dev/docs/cli/mcp/) | [kiro.dev/docs/cli/mcp/security/](https://kiro.dev/docs/cli/mcp/security/)

---

## Configuration Best Practices

### Use Descriptive Names

```json
{
  "mcpServers": {
    "aws-docs": { ... },
    "github-integration": { ... },
    "project-db": { ... }
  }
}
```

Usá nombres descriptivos que reflejen el propósito del servidor.

### Scope Appropriately

| Ámbito | Cuándo usarlo |
|---|---|
| **Global** (`~/.kiro/settings/mcp.json`) | Servidores que usás en todos los proyectos (AWS docs, GitHub) |
| **Project** (`.kiro/settings/mcp.json`) | Servidores específicos del proyecto (DB local, API interna) |
| **Agent** (en el JSON del agente) | Servidores exclusivos de un workflow específico |

### Set Appropriate Timeouts

```json
{
  "mcpServers": {
    "slow-server": {
      "command": "slow-command",
      "args": [],
      "timeout": 300000
    }
  }
}
```

Aumentá el timeout para servidores que tardan en iniciar.

---

## Tool Management

### Use `allowedTools` for Common Operations

```json
{
  "allowedTools": ["@aws-docs/search_documentation", "@aws-docs/read_documentation"]
}
```

Pre-aprobá tools de uso frecuente para reducir interrupciones.

### Resolve Name Conflicts with Aliases

```json
{
  "toolAliases": {
    "@github-mcp/get_issues": "github_issues",
    "@gitlab-mcp/get_issues": "gitlab_issues"
  }
}
```

---

## Performance Best Practices

- **Deshabilitar servidores no usados**: Usá `"disabled": true` en lugar de eliminar la configuración
- **Limitar el número de servidores**: Cada servidor agrega overhead — solo cargá los necesarios
- **Monitorear descripciones grandes**: Si una tool tiene descripción >10,000 caracteres, puede afectar el rendimiento
- **Usar `includeMcpJson: false`** en agentes que no necesitan acceso a todos los servidores globales

---

## Development Workflow

```bash
# 1. Agregar un nuevo servidor
kiro-cli mcp add --name my-server --command my-command --scope global

# 2. Listar servidores configurados
kiro-cli mcp list

# 3. Verificar que las tools están disponibles (en chat)
/tools

# 4. Ver logs de MCP para troubleshooting
# Output panel → "Kiro - MCP Logs"
```

---

## MCP Server Loading Priority

Cuando `includeMcpJson: true` en un agente:
1. Servers del agente (`mcpServers` en el JSON del agente)
2. Servers del proyecto (`.kiro/settings/mcp.json`)
3. Servers globales (`~/.kiro/settings/mcp.json`)

En caso de conflicto de nombres, prevalece el servidor del agente.

Ver [Configuration →](../03_Chat/13_Configuration.md) para más detalles sobre prioridad de configuración.