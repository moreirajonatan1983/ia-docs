# MCP — Agent Sandbox

> **Source:** [kiro.dev/docs/autonomous-agent/sandbox/mcp/](https://kiro.dev/docs/autonomous-agent/sandbox/mcp/)

---

Los servidores MCP (Model Context Protocol) pueden configurarse en el sandbox del Autonomous Agent para extender sus capacidades con tools externas.

---

## Configuration

Los servidores MCP se configuran en el archivo de configuración MCP del sandbox. La configuración se carga cuando el sandbox inicia y permanece disponible durante toda la ejecución de la tarea.

### Example Configuration

```json
{
  "mcpServers": {
    "aws-knowledge-mcp-server": {
      "command": "uvx",
      "args": [
        "fastmcp",
        "run",
        "https://knowledge-mcp.global.api.aws"
      ],
      "env": {}
    }
  }
}
```

---

## Supported Servers

> **Limitación actual:** Solo se soportan **servidores MCP locales**. Los servidores MCP remotos no están disponibles en este momento.

---

## Using Environment Variables and Secrets

Podés referenciar [environment variables y secrets](./02_Environment%20Variables.md) en tu configuración MCP para pasar credenciales y valores de configuración de forma segura.

Usá la sintaxis `${key_name}` para referenciar las keys:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "executable",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR_KEY": "${my_env_var_key}",
        "SECRET_KEY":  "${my_secret_key}"
      }
    }
  }
}
```

Tanto las environment variables como los secrets usan la misma sintaxis. Los valores se resuelven cuando el sandbox inicia.

---

## Related

- [Environment Variables →](./02_Environment%20Variables.md)
- [Environment Configuration →](./04_Environment%20Configuration.md)