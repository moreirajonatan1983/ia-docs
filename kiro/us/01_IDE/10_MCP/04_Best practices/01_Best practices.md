# MCP Best Practices

> **Source:** [kiro.dev/docs/mcp/security/](https://kiro.dev/docs/mcp/security/)

---

## Secure Configuration

### Protecting API Keys and Tokens

1. **Nunca commitees** archivos de configuración con tokens sensibles a control de versiones
2. Creá tokens con **permisos mínimos** necesarios para el MCP server (ej. usa fine-grained personal access tokens para GitHub en lugar de classic tokens)
3. Limitá el scope de acceso solo a los repositorios o recursos necesarios
4. **Rotá regularmente** las API keys y tokens usados en configuraciones
5. Usá **variables de entorno** siempre que sea posible en lugar de hardcodear valores

### Example: Using Environment Variables

En lugar de hardcodear tokens:

```json
{
  "mcpServers": {
    "github": {
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}"
      }
    }
  }
}
```

Configurá la variable de entorno en tu shell:

```bash
export GITHUB_TOKEN=your-token-value
```

### Approved Environment Variables

Por seguridad, Kiro solo expande variables de entorno **explícitamente aprobadas**. Cuando agregás o modificás una configuración MCP con variables no aprobadas, Kiro muestra un popup de advertencia.

Para gestionar las variables aprobadas:
1. Abrí Kiro Settings
2. Buscá **"Mcp Approved Env Vars"**
3. Agregá las variables que querés permitir

### Configuration File Permissions

Restringí el acceso a tus archivos de configuración MCP:

```bash
# Configuración a nivel usuario
chmod 600 ~/.kiro/settings/mcp.json

# Configuración a nivel workspace
chmod 600 .kiro/settings/mcp.json
```

---

## Safe Tool Usage

### Tool Approval Process

1. Revisá cada request de tool cuidadosamente antes de aprobar
2. Verificá los parámetros que se pasan al tool
3. Entendé qué va a hacer el tool antes de aprobar
4. Denegá cualquier request sospechoso que no coincida con tu tarea actual

### Auto-Approval Guidelines

Solo auto-aprobá tools que:
1. No tienen acceso de escritura a sistemas sensibles
2. Provienen de fuentes de confianza con código verificado
3. Son de uso frecuente en tu workflow
4. Tienen scope limitado de acceso

```json
{
  "mcpServers": {
    "aws-docs": {
      "autoApprove": [
        "mcp_aws_docs_search_documentation",
        "mcp_aws_docs_read_documentation"
      ]
    }
  }
}
```

---

## Workspace Isolation

### Using Workspace-Level Configurations

Para proyectos con diferentes requisitos de seguridad, usá configuraciones a nivel workspace (`.kiro/settings/mcp.json`) en lugar de la configuración global del usuario:

- Limitá los MCP servers disponibles por proyecto
- Configurá permisos específicos por workspace
- Evitá exponer servers de producción en proyectos de desarrollo

---

## Monitoring and Auditing

### Checking MCP Logs

Revisá regularmente los logs MCP para monitorear la actividad del server:

1. Abrí el panel de Kiro
2. Seleccioná la pestaña **Output**
3. Elegí **"Kiro - MCP Logs"** del dropdown

### Auditing Tool Usage

Periódicamente revisá qué tools has aprobado:

1. Verificá tu configuración MCP para tools auto-aprobados
2. Revisá los logs MCP para patrones de uso
3. Monitoreá la actividad del server en busca de comportamiento inesperado
4. Remové el auto-approval para tools que ya no usás frecuentemente

---

## Responding to Security Incidents

Si sospechás que un MCP server fue comprometido o está actuando de forma inesperada:

1. **Deshabilitar el server** inmediatamente: `"disabled": true` en la configuración
2. **Revocar tokens** comprometidos desde la plataforma correspondiente (GitHub, AWS, etc.)
3. **Revisar logs** para entender el alcance del problema
4. **Rotar credenciales** antes de re-habilitar el server

---

## Additional Security Measures

### Network Security

- Conectate solo a servers remotos con HTTPS
- Verificá certificados SSL de endpoints remotos
- Considerá usar un proxy corporativo para servidores remotos en entornos enterprise

### System Security

- Mantené actualizados los paquetes npm/uvx de los MCP servers
- Revisá los changelogs de servidores MCP antes de actualizar
- Ejecutá servidores MCP con permisos mínimos del sistema operativo