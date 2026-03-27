# Seguridad MCP

> **Fuente:** [kiro.dev/docs/cli/mcp/security/](https://kiro.dev/docs/cli/mcp/security/)

---

## Consideraciones de seguridad

### Confianza y verificación
- Solo instala servidores MCP de **fuentes confiables**
- Revisará las descripciones de las herramientas y la documentación antes de instalar.
- Verifica avisos de seguridad y actualizaciones

### Control de acceso
- Usamos principios de **mínimo privilegio** para los permisos del servidor
- Limitá el acceso al sistema de archivos a los directorios necesarios únicamente
- Restringí el acceso a la red donde sea posible
- Usamos variables de entorno para credenciales sensibles

### Gestión de credenciales
- **Nunca** codifica claves API o tokens en archivos de configuración
- Usamos variables de entorno para datos sensibles.
- Rotá las credenciales regularmente
- Almacená credenciales de forma segura usando el llavero del sistema

### Seguridad de la red
- Usa HTTPS para servidores remotos MCP
- Verifica certificados SSL/TLS
- Sé cauteloso con servidores que requieren acceso amplio a la red
- Monitoreá el tráfico de red para actividad inusual

### Monitoreo y Auditoría
- Revisará los registros del servidor MCP periódicamente
- Monitoreá comportamientos inesperados
- Llevá registro de los servidores instalados y sus permisos
- Elimina servidores no usados o no confiables rápidamente

---

## Seguridad de configuración

```golpecito
# Usamos variables de entorno para datos sensibles
exportar MCP_API_KEY="tu-clave-segura"
exportar DATABASE_URL="tu-cadena-de-conexión"

# Configurará el servidor MCP con variables de entorno
kiro-cli mcp agregar mi-servidor --env MCP_API_KEY --env DATABASE_URL
```

**`mcp.json` — forma correcta:**
```json
{
  "mcpServers": {
    "mi-servidor": {
      "comando": "comando-mi-servidor",
      "entorno": {
        "API_KEY": "$MCP_API_KEY"
      }
    }
  }
}
```

> ⚠️ Nunca comités archivos de configuración con claves API codificadas. Agregue `mcp.json` a `.gitignore` si contiene datos sensibles.

---

## Resumen de mejores prácticas

| Práctica | Descripción |
|---|---|
| Fuentes confiables | Solo instalar servidores verificados |
| Variables de entorno | Para todas las credenciales |
| Mínimo privilegio | Solo los permisos necesarios |
| Monitoreo activo | Revisar registros periódicamente |
| Removedor no usado | Eliminar servidores obsoletos |
| Usar HTTPS | Para servidores remotos |