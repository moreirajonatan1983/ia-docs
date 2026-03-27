# MCP Registry

> **Source:** [kiro.dev/docs/cli/mcp/examples/](https://kiro.dev/docs/cli/mcp/examples/)

---

## Available MCP Servers

### AWS Documentation Server

Proporciona acceso a la documentación de AWS, capacidades de búsqueda y recomendaciones.

**Capacidades:**
- Buscar documentación de AWS en todos los servicios
- Leer páginas de documentación en formato Markdown
- Obtener recomendaciones de contenido relacionado

**Setup (macOS/Linux):**
```json
{
  "mcpServers": {
    "aws-docs": {
      "command": "uvx",
      "args": ["awslabs.aws-documentation-mcp-server@latest"],
      "env": { "FASTMCP_LOG_LEVEL": "ERROR" },
      "disabled": false
    }
  }
}
```

**Setup (Windows):**
```json
{
  "mcpServers": {
    "aws-docs": {
      "command": "uv",
      "args": ["tool", "run", "--from", "awslabs.aws-documentation-mcp-server@latest", "awslabs.aws-documentation-mcp-server.exe"],
      "env": { "FASTMCP_LOG_LEVEL": "ERROR" }
    }
  }
}
```

**Uso:**
```
Search AWS documentation for S3 bucket policies
Read the AWS Lambda function URLs documentation
Find related content to AWS ECS task definitions
```

---

### GitHub MCP Server

Permite interactuar con repositorios, issues y pull requests de GitHub.

**Setup:**
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

---

### Database Servers

| Server | Descripción |
|---|---|
| PostgreSQL MCP Server | Query y gestión de bases de datos PostgreSQL |
| MongoDB MCP Server | Interacción con bases de datos MongoDB |

### Development Tools

| Server | Descripción |
|---|---|
| Docker MCP Server | Gestión de containers e imágenes Docker |
| Kubernetes MCP Server | Interacción con clusters Kubernetes |

---

## Finding More MCP Servers

- [MCP Registry](https://github.com/modelcontextprotocol/registry)
- [GitHub MCP Organization](https://github.com/modelcontextprotocol)
- Buscar `mcp-server` en npm o PyPI

---

## Creating a Custom Server

1. Elegí un lenguaje (Python, Node.js, etc.)
2. Implementá el protocolo MCP usando las librerías disponibles
3. Definí tus tools y sus capacidades
4. Empaquetá y distribuí tu servidor

**Recursos:**
- [MCP Protocol Specification](https://modelcontextprotocol.io/specification/2025-06-18)
- [Official MCP Documentation](https://modelcontextprotocol.io/introduction)