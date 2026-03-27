# Protocolo de contexto modelo (MCP): CLI

> **Fuente:** [kiro.dev/docs/cli/mcp/](https://kiro.dev/docs/cli/mcp/)

---

MCP es un protocolo que permite a Kiro comunicarse con servidores externos para acceder a información y herramientas especializadas.

Con MCP, puedes:
- Acceda a bases de conocimiento y documentación especializadas.
- Integrar con servicios externos y API.
- Amplíe las capacidades de Kiro con herramientas específicas de dominio
- Cree herramientas personalizadas para sus flujos de trabajo específicos

---

## Configuración de MCP

Hay dos formas de configurar servidores MCP en Kiro CLI:

### 1. Línea de comando

```bash
kiro-cli mcp add \
  --name "awslabs.aws-documentation-mcp-server" \
  --scope global \
  --command "uvx" \
  --args "awslabs.aws-documentation-mcp-server@latest" \
  --env "FASTMCP_LOG_LEVEL=ERROR" \
  --env "AWS_DOCUMENTATION_PARTITION=aws"
```

### 2. Archivo mcp.json

Los servidores MCP se pueden cargar desde:
- Nivel de Workspace: `<raíz del proyecto>/.kiro/settings/mcp.json`
- Nivel de usuario: `~/.kiro/settings/mcp.json`

```json
{
  "mcpServers": {
    "local-server-name": {
      "command": "command-to-run-server",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR1": "value1",
        "ENV_VAR2": "value2"
      },
      "disabled": false
    },
    "http-server-with-oauth": {
      "type": "http",
      "url": "https://api.example.com/mcp",
      "oauth": {
        "redirectUri": "127.0.0.1:8080",
        "oauthScopes": ["read", "write"]
      }
    }
  }
}
```

Para servidores MCP basados en HTTP que requieren OAuth:
- `oauth.redirectUri` — URI de redireccionamiento personalizado para flujo OAuth (opcional)
- `oauth.oauthScopes`: conjunto de alcances de OAuth para solicitar (opcional)

> Si encuentra errores de alcance de OAuth, utilice una matriz vacía: `"oauthScopes": []`

### 3. Configuración del agente

El campo `mcpServers` especifica a qué servidores MCP tiene acceso un agente personalizado:

```json
{
  "name": "myagent",
  "description": "My special agent",
  "mcpServers": {
    "fetch": {
      "command": "fetch3.1",
      "args": []
    }
  },
  "includeMcpJson": false
}
```

> `includeMcpJson: true` le da al agente acceso a todos los servidores MCP definidos en las configuraciones a nivel de usuario y Workspace, además de aquellos en el campo `mcpServers` del agente.

---

## Solución de problemas

### Errores de validación de herramientas

Verifique que el servidor MCP esté ejecutándose y sea accesible. Consulte la documentación del servidor para conocer la configuración requerida.

### Advertencias de descripción grande

Algunos servidores MCP proporcionan descripciones de herramientas muy extensas. Esto puede afectar el rendimiento. Considere utilizar un servidor más específico o herramientas de filtrado si están disponibles.

---

## Recursos adicionales

- [Registro del servidor MCP →](https://kiro.dev/docs/cli/mcp/registry/)
- [Ejemplos de MCP →](https://kiro.dev/docs/cli/mcp/examples/)
- [Seguridad de MCP →](https://kiro.dev/docs/cli/mcp/security/)