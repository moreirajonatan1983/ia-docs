# MCP Configuration

> **Source:** [kiro.dev/docs/mcp/configuration/](https://kiro.dev/docs/mcp/configuration/)

---

## Configuration File Structure

Los archivos de configuración MCP usan formato JSON:

```json
{
  "mcpServers": {
    "local-server-name": {
      "command": "command-to-run-server",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR1": "hard-coded-variable",
        "ENV_VAR2": "${EXPANDED_VARIABLE}"
      },
      "disabled": false,
      "autoApprove": ["tool_name1", "tool_name2"],
      "disabledTools": ["tool_name3"]
    },
    "remote-server-name": {
      "url": "https://endpoint.to.connect.to",
      "headers": {
        "HEADER1": "value1",
        "HEADER2": "value2"
      },
      "disabled": false,
      "autoApprove": ["tool_name1", "tool_name2"],
      "disabledTools": ["tool_name3"]
    }
  }
}
```

### Configuration Properties

**Local server:**

| Propiedad | Descripción |
|---|---|
| `command` | Comando para iniciar el servidor |
| `args` | Argumentos del comando |
| `env` | Variables de entorno |
| `disabled` | `true` para deshabilitar sin eliminar |
| `autoApprove` | Tools aprobados automáticamente |
| `disabledTools` | Tools deshabilitados individualmente |

**Remote server:**

| Propiedad | Descripción |
|---|---|
| `url` | Endpoint del servidor remoto |
| `headers` | Headers HTTP (auth, etc.) |
| `disabled` | `true` para deshabilitar |
| `autoApprove` | Tools aprobados automáticamente |
| `disabledTools` | Tools deshabilitados |

---

## Configuration Locations

| Nivel | Archivo | Alcance |
|---|---|---|
| **Workspace** | `.kiro/settings/mcp.json` | Solo el workspace actual — ideal para servers específicos del proyecto |
| **User (global)** | `~/.kiro/settings/mcp.json` | Todos los workspaces — ideal para servers de uso frecuente |

> Si ambos archivos existen, las configuraciones se **mezclan** y el workspace tiene **precedencia**.

---

## Creating Configuration Files

### Using the Command Palette
`Cmd+Shift+P` → **"Kiro: Edit MCP Settings"**

### Using the Kiro Panel
Kiro Panel → MCP section → click en el ícono de configuración

---

## Environment Variables

Muchos MCP servers requieren variables de entorno para autenticación:

```json
{
  "mcpServers": {
    "server-name": {
      "env": {
        "API_KEY": "${YOUR_API_KEY}",
        "DEBUG": "true",
        "TIMEOUT": "30000"
      }
    }
  }
}
```

> ⚠️ Por seguridad, Kiro solo expande variables de entorno **explícitamente aprobadas**. Kiro muestra un popup de advertencia al detectar variables no aprobadas. Para gestionarlas: Settings → buscar **"Mcp Approved Env Vars"**.

---

## Disabling Servers Temporarily

Para deshabilitar un server sin eliminar su configuración:

```json
{
  "mcpServers": {
    "server-name": {
      "disabled": true
    }
  }
}
```

---

## Security Considerations

- Usá referencias a variables de entorno (`${API_TOKEN}`) en lugar de hardcodear valores sensibles
- Nunca commitees archivos de configuración con credenciales a control de versiones
- Conectate solo a servers remotos de confianza
- Revisá los permisos de los tools antes de agregarlos a `autoApprove`

---

## Troubleshooting Configuration Issues

| Problema | Solución |
|---|---|
| JSON inválido | Verificá sintaxis — comas, comillas, brackets |
| Comando no encontrado | Verificá que el comando existe en tu `PATH` |
| Variables no expandidas | Verificar que la variable está en la lista de aprobadas |
| Cambios no aplicados | Guardá el archivo (`Cmd+S`) — los servers se reconectan automáticamente |