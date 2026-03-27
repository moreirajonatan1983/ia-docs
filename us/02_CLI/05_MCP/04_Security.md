# MCP Security

> **Source:** [kiro.dev/docs/cli/mcp/security/](https://kiro.dev/docs/cli/mcp/security/)

---

## Security Considerations

### Trust and Verification
- Solo instalá MCP servers de **fuentes confiables**
- Revisá las descripciones de las tools y la documentación antes de instalar
- Verificá advisories de seguridad y actualizaciones

### Access Control
- Usá principios de **mínimo privilegio** para los permisos del servidor
- Limitá el acceso al filesystem a los directorios necesarios únicamente
- Restringí el acceso a la red donde sea posible
- Usá variables de entorno para credenciales sensibles

### Credential Management
- **Nunca** hardcodees API keys o tokens en archivos de configuración
- Usá variables de entorno para datos sensibles
- Rotá las credenciales regularmente
- Almacená credenciales de forma segura usando el keychain del sistema

### Network Security
- Usá HTTPS para servidores MCP remotos
- Verificá certificados SSL/TLS
- Sé cauteloso con servidores que requieren acceso amplio a la red
- Monitoreá el tráfico de red para actividad inusual

### Monitoring and Auditing
- Revisá los logs del servidor MCP regularmente
- Monitoreá comportamientos inesperados
- Llevá registro de los servidores instalados y sus permisos
- Eliminá servidores no usados o no confiables rápidamente

---

## Configuration Security

```bash
# Usá variables de entorno para datos sensibles
export MCP_API_KEY="your-secure-key"
export DATABASE_URL="your-connection-string"

# Configurá el servidor MCP con variables de entorno
kiro-cli mcp add my-server --env MCP_API_KEY --env DATABASE_URL
```

**`mcp.json` — forma correcta:**
```json
{
  "mcpServers": {
    "my-server": {
      "command": "my-server-command",
      "env": {
        "API_KEY": "$MCP_API_KEY"
      }
    }
  }
}
```

> ⚠️ Nunca commitees archivos de configuración con API keys hardcodeadas. Agregá `mcp.json` a `.gitignore` si contiene datos sensibles.

---

## Best Practices Summary

| Práctica | Descripción |
|---|---|
| Fuentes confiables | Solo instalar servers verificados |
| Variables de entorno | Para todas las credenciales |
| Mínimo privilegio | Solo los permisos necesarios |
| Monitoreo activo | Revisar logs regularmente |
| Remover no usados | Eliminar servers obsoletos |
| Usar HTTPS | Para servers remotos |