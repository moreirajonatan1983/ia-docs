# MCP Examples

> **Source:** [kiro.dev/docs/cli/mcp/examples/](https://kiro.dev/docs/cli/mcp/examples/)

---

## AWS Documentation Server — Full Setup

### Prerequisites

```bash
# macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows PowerShell
irm https://astral.sh/uv/install.ps1 | iex

# Instalar Python 3.10+
uv python install 3.10
```

### Configuration

**Vía CLI:**
```bash
kiro-cli mcp add \
  --name "awslabs.aws-documentation-mcp-server" \
  --scope global \
  --command "uvx" \
  --args "awslabs.aws-documentation-mcp-server@latest" \
  --env "FASTMCP_LOG_LEVEL=ERROR" \
  --env "AWS_DOCUMENTATION_PARTITION=aws"
```

**Vía `mcp.json`:**
```json
{
  "mcpServers": {
    "aws-docs": {
      "command": "uvx",
      "args": ["awslabs.aws-documentation-mcp-server@latest"],
      "env": { "FASTMCP_LOG_LEVEL": "ERROR" },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

### Usage
```
Search AWS documentation for S3 bucket policies
Read the AWS Lambda function URLs documentation
Get recommendations for AWS ECS task definitions
```

---

## GitHub MCP Server — Full Setup

### Capabilities
- Gestión de repositorios, issues y pull requests
- Búsqueda de código en GitHub
- Operaciones de branches y commits

### Setup
```bash
kiro-cli mcp add \
  --name "github" \
  --command "npx" \
  --args "-y @modelcontextprotocol/server-github" \
  --env "GITHUB_PERSONAL_ACCESS_TOKEN=<tu-token>"
```

### Configuration
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "<token>" }
    }
  }
}
```

Token scopes requeridos: `repo`, `user`.

### Common Tools
- `list_issues` — Listar issues de un repositorio
- `create_pull_request` — Crear un PR
- `search_code` — Buscar código

---

## HTTP MCP Server with OAuth

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

Si encontrás errores de OAuth scope, usá un array vacío: `"oauthScopes": []`

---

## Custom MCP Server

### Structure Example (Python)
```python
from mcp import Server, Tool

server = Server("my-custom-server")

@server.tool()
def my_tool(query: str) -> str:
    """Describe what this tool does"""
    return f"Result for: {query}"
```

Ver la [especificación del protocolo MCP](https://modelcontextprotocol.io/specification/2025-06-18) para detalles.