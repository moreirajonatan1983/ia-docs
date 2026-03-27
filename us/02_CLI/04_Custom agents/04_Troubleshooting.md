# Troubleshooting Custom Agents

> **Source:** [kiro.dev/docs/cli/custom-agents/troubleshooting/](https://kiro.dev/docs/cli/custom-agents/troubleshooting/)

---

## Configuration Errors

### Invalid JSON Syntax

**Síntomas:**
- Mensajes de error mencionando "invalid JSON" o "syntax error"
- El agente no aparece en `/agent list`
- Comportamiento de fallback al agente por defecto

**Soluciones:**
- Validá el JSON con un linter online
- Revisá errores comunes de JSON:
  - Comas faltantes entre elementos
  - Comas al final del último elemento (trailing commas)
  - Brackets o llaves sin cerrar
  - Comillas sin escapar en strings
- Usá `/agent schema` para verificar la estructura de tu configuración

### Schema Validation Errors

**Síntomas:**
- Warnings sobre campos desconocidos
- Comportamiento que no coincide con la configuración
- Errores de campos requeridos faltantes

**Soluciones:**
- Compará tu configuración contra el schema con `/agent schema`
- Buscá typos en nombres de campos (ej. `allowedTools` vs `allowedTool`)
- Verificá que los tipos de datos coincidan (arrays vs strings, booleans vs strings)

---

## Custom Agent Loading Issues

### Agent Not Found

**Síntomas:**
- `/agent list` no muestra tu agente
- Fallback al agente por defecto sin advertencia

**Soluciones:**
- Verificá la ubicación del archivo:
  - Global: `~/.kiro/agents/<name>.json`
  - Workspace: `.kiro/agents/<name>.json`
- Verificá permisos de lectura del archivo
- Asegurate de que el nombre del archivo coincide con el nombre que intentás usar
- El archivo debe tener extensión `.json`

### Wrong Agent Version Loading

**Síntomas:**
- El comportamiento no coincide con los cambios recientes de configuración
- Warning sobre conflictos de agentes

**Soluciones:**
- Los agentes locales tienen precedencia sobre los globales
- Usá `/agent list` para ver qué versión está cargada
- Renombrá o eliminá archivos de agentes en conflicto

---

## Tool Issues

### Tool Not Available

**Síntomas:**
- Errores sobre tools desconocidas o no disponibles
- El agente pide permiso para tools en `allowedTools`
- Tools de MCP servers no funcionan

**Soluciones:**
- Verificá que los nombres de las tools estén correctamente escritos en el array `tools`
- Para tools MCP, asegurate de que el servidor está configurado en `mcpServers`
- Usá la sintaxis correcta: `@server_name/tool_name`

### Unexpected Permission Prompts

**Síntomas:**
- Prompts de permiso para tools listadas en `allowedTools`

**Soluciones:**
- Asegurate de que las tools están en **ambos** arrays: `tools` Y `allowedTools`
- Revisá typos entre los dos arrays
- Para tools MCP, usá el nombre completo con prefijo del servidor en `allowedTools`
- Verificá que los `toolAliases` estén correctamente aplicados

---

## Debugging Agent Behavior

### Testing Checklist

```
1. Validar JSON: usar un JSON validator
2. Verificar schema: /agent schema
3. Listar agentes: /agent list
4. Cambiar al agente: /agent swap [nombre]
5. Testear cada tool individualmente
6. Verificar resources y hooks
7. Testear workflows completos
```

### MCP Server Issues

- Verificá que los comandos del servidor MCP son correctos y los ejecutables están en tu PATH
- Verificá que las variables de entorno requeridas están seteadas
- Testea los servidores MCP de forma independiente
- Revisá los logs del servidor MCP para mensajes de error
- Aumentá los valores de `timeout` si los servidores tardan en iniciar