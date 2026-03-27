# Protocolo de contexto modelo (MCP)

> **Fuente:** [kiro.dev/docs/mcp/](https://kiro.dev/docs/mcp/)

---

MCP es un protocolo que permite a Kiro comunicarse con servidores externos para acceder a herramientas, indicaciones y recursos especializados. Por ejemplo, el servidor MCP de documentación de AWS proporciona herramientas para buscar, leer y obtener recomendaciones de la documentación de AWS directamente dentro de Kiro.

Con MCP, puedes:
- Acceda a bases de conocimiento y documentación especializadas.
- Integrar con servicios externos y API.
- Amplíe las capacidades de Kiro con herramientas específicas de dominio
- Utilice plantillas de mensajes y plantillas de recursos proporcionadas por el servidor a través del sistema de menciones `#` en el chat.
- Responder a las solicitudes de obtención del servidor cuando las herramientas necesitan información adicional durante la ejecución.
- Cree herramientas personalizadas para sus flujos de trabajo específicos

---

## Configuración de MCP

### Requisitos previos

Antes de usar MCP:
1. Asegúrate de tener instalada la última versión de Kiro.
2. Consulte la documentación de cada servidor MCP para conocer los requisitos previos específicos.

### Habilitación del soporte MCP

Después de crear su archivo de configuración:
1. Abra Configuración con `Cmd+` (Mac) o `Ctrl+` (Windows/Linux)
2. Busque "MCP"
3. Habilite la configuración de soporte de MCP

### Uso de la pestaña Servidores MCP

El panel Kiro incluye una **pestaña de servidores MCP** que muestra:
- Todos los servidores MCP configurados
- Indicadores de estado de conexión
- Acceso rápido a las herramientas del servidor.

Para utilizar esta función:
1. Selecciona el ícono de Kiro en la barra de actividades.
2. Navegue a la pestaña **Servidores MCP**
3. Haga clic en el nombre de cualquier herramienta para insertar un mensaje de marcador de posición en el chat.

---

## Configuración

Los archivos de configuración de MCP utilizan el formato JSON:

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
      "autoApprove": ["tool_name1"],
      "disabledTools": ["tool_name3"]
    }
  }
}
```

### Ubicaciones de configuración

| Nivel | Archivo | Alcance |
|---|---|---|
| **Espacio de trabajo** | `.kiro/settings/mcp.json` | Solo espacio de trabajo actual: ideal para servidores de proyectos específicos |
| **Usuario** | `~/.kiro/settings/mcp.json` | Todos los espacios de trabajo: lo mejor para servidores de uso frecuente |

> Si ambos archivos existen, las configuraciones se **fusionan** y la configuración del espacio de trabajo tiene prioridad.

### Creando archivos de configuración

- **Paleta de comandos:** `Cmd+Shift+P` → buscar "MCP" → "Kiro: Configurar servidores MCP"
- **Panel Kiro:** Navegue a la pestaña de servidores MCP → haga clic en **+** para agregar un nuevo servidor

### Variables de entorno

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

### Deshabilitar servidores temporalmente

```json
{
  "mcpServers": {
    "server-name": {
      "disabled": true
    }
  }
}
```

### Consideraciones de seguridad

- Utilice referencias de variables de entorno ("${API_TOKEN}`) en lugar de codificar valores sensibles
- Nunca envíe archivos de configuración con credenciales al control de versiones.
- Conéctese únicamente a servidores remotos confiables
- Revisar los permisos de la herramienta antes de agregarlos a "autoApprove".

---

## Solución de problemas

### Problemas de configuración comunes

1. **Valide la sintaxis JSON**: asegúrese de que no haya errores de sintaxis, comas, comillas o corchetes faltantes.
2. **Verificar rutas de comando**: asegúrese de que el comando exista en su RUTA; intenta ejecutarlo directamente en tu terminal
3. **Verifique las variables de entorno**: verifique que las variables de entorno requeridas estén configuradas y tengan el nombre correcto
4. **Guardar cambios de configuración**: los cambios se aplican automáticamente al guardar (`Cmd+S`)

### Comprobación de registros de MCP

1. Abre el panel de Kiro
2. Seleccione la pestaña **Salida**
3. Elija **"Kiro - Registros de MCP"** en el menú desplegable.

---

## Próximos pasos

- [Configuración de MCP →](https://kiro.dev/docs/mcp/configuration/)
- [Gestión del servidor MCP →](https://kiro.dev/docs/mcp/servers/)
- [Uso de herramientas MCP →](https://kiro.dev/docs/mcp/usage/)
- [Mejores prácticas / Seguridad →](https://kiro.dev/docs/mcp/security/)
- [Documentación oficial de MCP →](https://modelcontextprotocol.io/introduction)