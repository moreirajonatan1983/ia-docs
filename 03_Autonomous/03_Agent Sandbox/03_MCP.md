# MCP: Agente Sandbox

> **Fuente:** [kiro.dev/docs/autonomous-agent/sandbox/mcp/](https://kiro.dev/docs/autonomous-agent/sandbox/mcp/)

---

Los servidores MCP (Model Context Protocol) pueden configurarse en el sandbox del Agente Autónomo para ampliar sus capacidades con herramientas externas.

---

## Configuración

Los servidores MCP se configuran en el archivo de configuración MCP del sandbox. La configuración se carga cuando el sandbox inicia y permanece disponible durante toda la ejecución de la tarea.

### Ejemplo de configuración

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

## Servidores compatibles

> **Limitación actual:** Solo se soportan **servidores locales MCP**. Los servidores MCP remotos no están disponibles en este momento.

---

## Uso de variables y secretos de entorno

Podés referenciar [variables de entorno y secretos](./02_Environment%20Variables.md) en tu configuración MCP para pasar credenciales y valores de configuración de forma segura.

Usaremos la sintaxis `${key_name}` para referenciar las claves:

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

Tanto las variables de entorno como los secretos usan la misma sintaxis. Los valores se resuelven cuando se inicia el sandbox.

---

## Relacionado

- [Variables de entorno →](./02_Environment%20Variables.md)
- [Configuración del entorno →](./04_Environment%20Configuration.md)