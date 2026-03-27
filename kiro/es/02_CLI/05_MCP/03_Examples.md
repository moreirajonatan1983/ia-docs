# Ejemplos de MCP

> **Fuente:** [kiro.dev/docs/cli/mcp/examples/](https://kiro.dev/docs/cli/mcp/examples/)

---

## Servidor de documentación de AWS: configuración completa

### Requisitos previos

```golpecito
#macOS/Linux
rizo -LsSf https://astral.sh/uv/install.sh | sh

#WindowsPowerShell
irm https://astral.sh/uv/install.ps1 | iex

# Instalar Python 3.10+
instalación uv python 3.10
```

### Configuración

**Vía CLI:**
```golpecito
kiro-cli mcp agregar \
  --nombre "awslabs.aws-documentation-mcp-server" \
  --alcance global \
  --comando "uvx" \
  --args "awslabs.aws-documentation-mcp-server@latest" \
  --env "FASTMCP_LOG_LEVEL=ERROR" \
  --env "AWS_DOCUMENTATION_PARTITION=aws"
```

**Vía `mcp.json`:**
```json
{
  "mcpServers": {
    "docs-aws": {
      "comando": "uvx",
      "args": ["awslabs.aws-documentation-mcp-server@latest"],
      "entorno": { "FASTMCP_LOG_LEVEL": "ERROR" },
      "deshabilitado": falso,
      "aprobación automática": []
    }
  }
}
```

### Uso
```
Busque en la documentación de AWS las políticas del depósito S3
Lea la documentación de las URL de la función AWS Lambda
Obtenga recomendaciones para definiciones de tareas de AWS ECS
```

---

## Servidor GitHub MCP: configuración completa

### Capacidades
- Gestión de repositorios, issues y pull request.
- Búsqueda de código en GitHub
- Operaciones de sucursales y commits.

### Configuración
```golpecito
kiro-cli mcp agregar \
  --nombre "github" \
  --comando "npx" \
  --args "-y @modelcontextprotocol/servidor-github" \
  --env "GITHUB_PERSONAL_ACCESS_TOKEN=<tu-token>"
```

### Configuración
```json
{
  "mcpServers": {
    "github": {
      "comando": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "<token>" }
    }
  }
}
```

Alcances de token requeridos: `repo`, `user`.

### Herramientas comunes
- `list_issues` — Listar issues de un repositorio
- `create_pull_request` — Crear un PR
- `search_code` — Buscar código

---

## Servidor HTTP MCP con OAuth

```json
{
  "mcpServers": {
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

Si encuentra errores de alcance de OAuth, use un array vacío: `"oauthScopes": []`

---

## Servidor MCP personalizado

### Ejemplo de estructura (Python)
```pitón
desde mcp import Server, Herramienta

servidor = Servidor("mi-servidor-personalizado")

@servidor.herramienta()
def my_tool(consulta: str) -> str:
    """Describe lo que hace esta herramienta"""
    return f"Resultado de: {consulta}"
```

Ver la [spec del protocolo MCP](https://modelcontextprotocol.io/specification/2025-06-18) para detalles.