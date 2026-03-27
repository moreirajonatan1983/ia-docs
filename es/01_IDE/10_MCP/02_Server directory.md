# Directorio del servidor MCP

> **Fuente:** [kiro.dev/docs/mcp/servers/](https://kiro.dev/docs/mcp/servers/)

---

## Servidores disponibles

Kiro incluye un directorio curador de servidores MCP con instalación con un clic. Podés explorarlos directamente en el panel de Kiro o en [kiro.dev/docs/mcp/servers/](https://kiro.dev/docs/mcp/servers/).

### Servidores destacados

| Servidor | Comando de instalacion | Requerir |
|---|---|---|
| **Documentos de AWS** | `uvx awslabs.aws-documentation-mcp-server@latest` | UV |
| **GitHub** | URL: `https://api.githubcopilot.com/mcp/` | Ficha |
| **Contexto7** | `npx -y @upstash/context7-mcp` | Nodo |
| **Git** | `uvx mcp-servidor-git` | UV |
| **Acoplador** | `npx -y @modelcontextprotocol/server-docker` | Nodo |
| **Sistema de archivos** | `npx -y @modelcontextprotocol/server-filesystem` | Nodo |
| **Azul** | `npx -y @modelcontextprotocol/server-azure` | Nodo + suscripción |
| **GCloud** | `npx -y @google-cloud/gcloud-mcp` | Nodo |
| **Perro de datos** | URL: `https://mcp.datadoghq.com/...` | Clave API |
| **Amplitud** | URL: `https://mcp.amplitude.com/mcp` | — |
| **Herramientas de desarrollo de Chrome** | `npx -y chrome-devtools-mcp@latest` | Nodo |
| **Dinatrace** | `npx -y @dynatrace-oss/dynatrace-mcp-server@latest` | Nodo + URL |

---

## Comparte tu servidor MCP

### Instalar esquema de enlace

Podés crear enlaces de instalación para que otros instalen tu servidor con un clic:

```
https://kiro.dev/launch/mcp/add?name=<server-name>&config=<url-encoded-config>
```

### Generar un enlace de instalación

**JavaScript/Mecanografiado:**
```javascript
función createKiroInstallLink(nombre, configuración) {
  const nombrecodificado = encodeURIComponent(nombre);
  const encodedConfig = encodeURIComponent(JSON.stringify(config));
  devolver `https://kiro.dev/launch/mcp/add?name=${encodedName}&config=${encodedConfig}`;
}

// Ejemplo: servidor local
enlace constante = createKiroInstallLink('aws-docs', {
  comando: 'uvx',
  argumentos: ['awslabs.aws-documentation-mcp-server@latest'],
  entorno: { FASTMCP_LOG_LEVEL: 'ERROR' },
  deshabilitado: falso,
  aprobación automática: []
});
```

**Python:**
```pitón
importar json
de urllib.parse cotización de importación

def create_kiro_install_link(nombre: str, configuración: dict) -> str:
    nombre_codificado = cita(nombre)
    codificado_config = cita (json.dumps (config))
    devolver f"https://kiro.dev/launch/mcp/add?name={encoded_name}&config={encoded_config}"
```

---

## Descubra más servidores MCP

### Recursos oficiales
- [Registro MCP](https://github.com/modelcontextprotocol/registry) — Registro oficial con servidores contribuyentes por la comunidad
- [Model Context Protocol Org](https://github.com/modelcontextprotocol) — Implementaciones de referencia del equipo MCP

### Registros de paquetes
- [npm](https://www.npmjs.com/search?q=mcp-server) — Buscar `mcp-server` o `@modelcontextprotocol/server-*`
- [PyPI](https://pypi.org/search/?q=mcp-server) — Buscar `mcp-server` para implementaciones Python