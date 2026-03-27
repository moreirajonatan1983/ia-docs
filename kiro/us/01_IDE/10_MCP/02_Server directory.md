# MCP Server Directory

> **Source:** [kiro.dev/docs/mcp/servers/](https://kiro.dev/docs/mcp/servers/)

---

## Available Servers

Kiro incluye un directorio curado de MCP servers con instalación con un clic. Podés explorarlos directamente en el panel de Kiro o en [kiro.dev/docs/mcp/servers/](https://kiro.dev/docs/mcp/servers/).

### Featured Servers

| Server | Comando de instalación | Requiere |
|---|---|---|
| **AWS Docs** | `uvx awslabs.aws-documentation-mcp-server@latest` | UV |
| **GitHub** | URL: `https://api.githubcopilot.com/mcp/` | Token |
| **Context7** | `npx -y @upstash/context7-mcp` | Node |
| **Git** | `uvx mcp-server-git` | UV |
| **Docker** | `npx -y @modelcontextprotocol/server-docker` | Node |
| **Filesystem** | `npx -y @modelcontextprotocol/server-filesystem` | Node |
| **Azure** | `npx -y @modelcontextprotocol/server-azure` | Node + suscripción |
| **GCloud** | `npx -y @google-cloud/gcloud-mcp` | Node |
| **Datadog** | URL: `https://mcp.datadoghq.com/...` | API key |
| **Amplitude** | URL: `https://mcp.amplitude.com/mcp` | — |
| **Chrome DevTools** | `npx -y chrome-devtools-mcp@latest` | Node |
| **Dynatrace** | `npx -y @dynatrace-oss/dynatrace-mcp-server@latest` | Node + URL |

---

## Share Your MCP Server

### Install Link Schema

Podés crear links de instalación para que otros instalen tu server con un clic:

```
https://kiro.dev/launch/mcp/add?name=<server-name>&config=<url-encoded-config>
```

### Generate an Install Link

**JavaScript/TypeScript:**
```javascript
function createKiroInstallLink(name, config) {
  const encodedName = encodeURIComponent(name);
  const encodedConfig = encodeURIComponent(JSON.stringify(config));
  return `https://kiro.dev/launch/mcp/add?name=${encodedName}&config=${encodedConfig}`;
}

// Ejemplo: server local
const link = createKiroInstallLink('aws-docs', {
  command: 'uvx',
  args: ['awslabs.aws-documentation-mcp-server@latest'],
  env: { FASTMCP_LOG_LEVEL: 'ERROR' },
  disabled: false,
  autoApprove: []
});
```

**Python:**
```python
import json
from urllib.parse import quote

def create_kiro_install_link(name: str, config: dict) -> str:
    encoded_name = quote(name)
    encoded_config = quote(json.dumps(config))
    return f"https://kiro.dev/launch/mcp/add?name={encoded_name}&config={encoded_config}"
```

---

## Discover More MCP Servers

### Official Resources
- [MCP Registry](https://github.com/modelcontextprotocol/registry) — Registry oficial con servidores contribuidos por la comunidad
- [Model Context Protocol Org](https://github.com/modelcontextprotocol) — Implementaciones de referencia del equipo MCP

### Package Registries
- [npm](https://www.npmjs.com/search?q=mcp-server) — Buscar `mcp-server` o `@modelcontextprotocol/server-*`
- [PyPI](https://pypi.org/search/?q=mcp-server) — Buscar `mcp-server` para implementaciones Python