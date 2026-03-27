# Registro MCP

> **Fuente:** [kiro.dev/docs/cli/mcp/examples/](https://kiro.dev/docs/cli/mcp/examples/)

---

## Servidores MCP disponibles

### Servidor de documentación de AWS

Proporciona acceso a la documentación de AWS, capacidades de búsqueda y recomendaciones.

**Capacidad:**
- Buscar documentación de AWS en todos los servicios
- Leer páginas de documentación en formato Markdown
- recomendaciones Obtener contenido relacionado

**Configuración (macOS/Linux):**
```json
{
  "mcpServers": {
    "docs-aws": {
      "comando": "uvx",
      "args": ["awslabs.aws-documentation-mcp-server@latest"],
      "entorno": { "FASTMCP_LOG_LEVEL": "ERROR" },
      "deshabilitado": falso
    }
  }
}
```

**Configuración (Windows):**
```json
{
  "mcpServers": {
    "docs-aws": {
      "comando": "uv",
      "args": ["herramienta", "ejecutar", "--from", "awslabs.aws-documentation-mcp-server@latest", "awslabs.aws-documentation-mcp-server.exe"],
      "env": { "FASTMCP_LOG_LEVEL": "ERROR" }
    }
  }
}
```

**Uso:**
```
Busque en la documentación de AWS las políticas del depósito S3
Lea la documentación de las URL de la función AWS Lambda
Encuentre contenido relacionado con las definiciones de tareas de AWS ECS
```

---

### Servidor MCP de GitHub

Permite interactuar con repositorios, issues y pull request de GitHub.

**Configuración:**
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

---

### Servidores de bases de datos

| Servidor | Descripción |
|---|---|
| Servidor MCP PostgreSQL | Consulta y gestión de bases de datos PostgreSQL |
| Servidor MCP MongoDB | Interacción con bases de datos MongoDB |

### Herramientas de desarrollo

| Servidor | Descripción |
|---|---|
| Servidor Docker MCP | Gestión de contenedores e imágenes Docker |
| Servidor Kubernetes MCP | Interacción con clusters Kubernetes |

---

## Encontrar más servidores MCP

- [Registro MCP] (https://github.com/modelcontextprotocol/registry)
- [Organización GitHub MCP](https://github.com/modelcontextprotocol)
- Buscar `mcp-server` en npm o PyPI

---

## Creando un servidor personalizado

1. Elegí un lenguaje (Python, Node.js, etc.)
2. Implementá el protocolo MCP usando las librerías disponibles
3. Defini tus herramientas y sus capacidades
4. Empaquetá y distribuiré tu servidor

**Recursos:**
- [Especificación del protocolo MCP] (https://modelcontextprotocol.io/specification/2025-06-18)
- [Documentación oficial de MCP] (https://modelcontextprotocol.io/introduction)