# Solución de problemas de agentes personalizados

> **Fuente:** [kiro.dev/docs/cli/custom-agents/troubleshooting/](https://kiro.dev/docs/cli/custom-agents/troubleshooting/)

---

## Errores de configuración

### Sintaxis JSON no válida

**Síntomas:**
- Mensajes de error mencionando "JSON no válido" o "error de sintaxis"
- El agente no aparece en `/lista de agentes`
- Comportamiento de respaldo al agente por defecto

**Soluciones:**
- Validá el JSON con un linter online
- Revisar errores comunes de JSON:
  - Comas faltantes entre elementos
  - Comas al final del último elemento (comas al final)
  - Soportes o llaves sin cerrar
  - Comillas sin escapar en cuerdas
- Usaremos `/agent Scheme` para verificar la estructura de tu configuración.

### Errores de validación del esquema

**Síntomas:**
- Advertencias sobre campos desconocidos
- Comportamiento que no coincide con la configuración
- Errores de campos requeridos faltantes

**Soluciones:**
- Comparará tu configuración contra el esquema con `/agent esquema`
- Buscá errores tipográficos en nombres de campos (ej. `allowedTools` vs `allowedTool`)
- Verifica que los tipos de datos coinciden (arrays vs strings, booleans vs strings)

---

## Problemas de carga del agente personalizado

### Agente no encontrado

**Síntomas:**
- `/lista de agentes` no muestra tu agente
- Fallback al agente por defecto sin advertencia

**Soluciones:**
- Verifique la ubicación del archivo:
  - Global: `~/.kiro/agents/<nombre>.json`
  - Espacio de trabajo: `.kiro/agents/<nombre>.json`
- Verifica permisos de lectura del archivo
- Asegurate de que el nombre del archivo coincida con el nombre que intentas usar
- El archivo debe tener extensión `.json`

### Cargando la versión incorrecta del agente

**Síntomas:**
- El comportamiento no coincide con los cambios recientes de configuración.
- Advertencia sobre conflictos de agentes

**Soluciones:**
- Los agentes locales tienen precedencia sobre los globales.
- Usaremos `/agent list` para ver qué versión está cargada
- Renombrá o eliminará archivos de agentes en conflicto

---

## Problemas con las herramientas

### Herramienta no disponible

**Síntomas:**
- Errores sobre herramientas desconocidas o no disponibles
- El agente pide permiso para herramientas en `allowedTools`
- Herramientas de servidores MCP no funcionan

**Soluciones:**
- Verifique que los nombres de las herramientas estén correctamente escritos en el array `tools`
- Para herramientas MCP, asegúrese de que el servidor esté configurado en `mcpServers`
- Usá la sintaxis correcta: `@server_name/tool_name`

### Solicitudes de permiso inesperadas

**Síntomas:**
- Solicita permiso para herramientas listadas en `allowedTools`

**Soluciones:**
- Asegurate de que las herramientas están en **ambos** arrays: `tools` Y `allowedTools`
- Revisá errores tipográficos entre los dos arrays.
- Para herramientas MCP, usará el nombre completo con prefijo del servidor en `allowedTools`
- Verifique que los `toolAliases` estén correctamente aplicados

---

## Comportamiento del agente de depuración

### Lista de verificación de pruebas

```
1. Validar JSON: usar un JSON validator
2. Verificar schema: /agent schema
3. Listar agentes: /agent list
4. Cambiar al agente: /agent swap [nombre]
5. Testear cada tool individualmente
6. Verificar resources y hooks
7. Testear workflows completos
```

### Problemas con el servidor MCP

- Verifica que los comandos del servidor MCP son correctos y los ejecutables están en tu PATH
- Verifique que las variables de entorno requeridas estén seleccionadas
- Testea los servidores MCP de forma independiente
- Revisará los logs del servidor MCP para mensajes de error
- Aumentá los valores de `timeout` si los servidores tardan en iniciar