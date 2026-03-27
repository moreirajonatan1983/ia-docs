# Mejores prácticas de MCP

> **Fuente:** [kiro.dev/docs/cli/mcp/](https://kiro.dev/docs/cli/mcp/) | [kiro.dev/docs/cli/mcp/security/](https://kiro.dev/docs/cli/mcp/security/)

---

## Mejores prácticas de configuración

### Utilizá nombres descriptivos

```json
{
  "mcpServers": {
    "aws-docs": { ... },
    "github-integration": { ... },
    "project-db": { ... }
  }
}
```

Usá nombres descriptivos que reflejan el propósito del servidor.

### Alcance apropiado

| Ámbito | Cuándo usarlo |
|---|---|
| **Global** (`~/.kiro/settings/mcp.json`) | Servidores que usamos en todos los proyectos (AWS docs, GitHub) |
| **Proyecto** (`.kiro/settings/mcp.json`) | Servidores específicos del proyecto (DB local, API interna) |
| **Agente** (en el JSON del agente) | Servidores exclusivos de un flujo de trabajo específico |

### Establecer tiempos de espera adecuados

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

Aumente el tiempo de espera para servidores que tardan en iniciarse.

---

## Gestión de herramientas

### Use `allowedTools` para operaciones comunes

```json
{
  "allowedTools": ["@aws-docs/search_documentation", "@aws-docs/read_documentation"]
}
```

Pre-aprobá herramientas de uso frecuente para reducir interrupciones.

### Resolver conflictos de nombres con alias

```json
{
  "toolAliases": {
    "@github-mcp/get_issues": "github_issues",
    "@gitlab-mcp/get_issues": "gitlab_issues"
  }
}
```

---

## Mejores prácticas de rendimiento

- **Deshabilitar servidores no usados**: Usá `"disabled": true` en lugar de eliminar la configuración
- **Limitar el número de servidores**: Cada servidor agrega sobrecarga — solo cargará los necesarios
- **Monitorear descripciones grandes**: Si una herramienta tiene descripción >10,000 caracteres, puede afectar el rendimiento
- **Usar `includeMcpJson: false`** en agentes que no necesitan acceso a todos los servidores globales

---

## Flujo de trabajo de desarrollo

```golpecito
# 1. Agregar un nuevo servidor
kiro-cli mcp agregar --nombre mi-servidor --comando mi-comando --alcance global

# 2. Listar servidores configurados
lista de mcp de kiro-cli

# 3. Verificar que las herramientas están disponibles (en chat)
/herramientas

# 4. Ver registros de MCP para solucionar problemas
# Panel de salida → "Kiro - Registros de MCP"
```

---

## Prioridad de carga del servidor MCP

Cuando `includeMcpJson: true` en un agente:
1. Servidores del agente (`mcpServers` en el JSON del agente)
2. Servidores del proyecto (`.kiro/settings/mcp.json`)
3. Servidores globales (`~/.kiro/settings/mcp.json`)

En caso de conflicto de nombres, prevalece el servidor del agente.

Ver [Configuración →](../03_Chat/13_Configuration.md) para más detalles sobre prioridad de configuración.