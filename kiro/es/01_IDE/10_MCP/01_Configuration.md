# Configuración de MCP

> **Fuente:** [kiro.dev/docs/mcp/configuration/](https://kiro.dev/docs/mcp/configuration/)

---

## Estructura del archivo de configuración

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

### Propiedades de configuración

**Servidor local:**

| Propiedad | Descripción |
|---|---|
| `comando` | Comando para iniciar el servidor |
| `argumentos` | Argumentos del comando |
| `entorno` | Variables de entorno |
| `deshabilitado` | `true` para deshabilitar sin eliminar |
| `aprobación automática` | Herramientas aprobadas automáticamente |
| `Herramientas deshabilitadas` | Herramientas deshabilitadas individualmente |

**Servidor remoto:**

| Propiedad | Descripción |
|---|---|
| `URL` | Punto final del servidor remoto |
| `encabezados` | Encabezados HTTP (autenticación, etc.) |
| `deshabilitado` | `true` para deshabilitar |
| `aprobación automática` | Herramientas aprobadas automáticamente |
| `Herramientas deshabilitadas` | Herramientas deshabilitadas |

---

## Ubicaciones de configuración

| Nivel | Archivo | Alcance |
|---|---|---|
| **Espacio de trabajo** | `.kiro/settings/mcp.json` | Solo el workspace actual — ideal para servidores específicos del proyecto |
| **Usuario (global)** | `~/.kiro/settings/mcp.json` | Todos los espacios de trabajo — ideales para servidores de uso frecuente |

> Si ambos archivos existen, las configuraciones se **mezclan** y el espacio de trabajo tiene **precedencia**.

---

## Creando archivos de configuración

### Usando la paleta de comandos
`Cmd+Shift+P` → **"Kiro: Editar configuración de MCP"**

### Usando el panel Kiro
Kiro Panel → sección MCP → haga clic en el ícono de configuración

---

## Variables de entorno

Muchos servidores MCP requieren variables de entorno para autenticación:

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

> ⚠️ Por seguridad, Kiro solo expande variables de entorno **explícitamente aprobadas**. Kiro muestra una ventana emergente de advertencia al detectar variables no aprobadas. Para gestionarlas: Configuración → buscar **"Mcp Approved Env Vars"**.

---

## Deshabilitar servidores temporalmente

Para deshabilitar un servidor sin eliminar su configuración:

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

## Consideraciones de seguridad

- Usá referencias a variables de entorno ("${API_TOKEN}`) en lugar de codificar valores sensibles
- Nunca comete archivos de configuración con credenciales a control de versiones
- Conectar solo a servidores remotos de confianza
- Revisará los permisos de las herramientas antes de agregarlos a `autoApprove`

---

## Solución de problemas de configuración

| Problema | Solución |
|---|---|
| JSON inválido | Verificá sintaxis — comas, comillas, corchetes |
| Comando no encontrado | Verifica que el comando existe en tu `PATH` |
| Variables no expandidas | Verificar que la variable está en la lista de aprobadas |
| Cambios no aplicados | Guardá el archivo (`Cmd+S`) — los servidores se reconectan automáticamente |