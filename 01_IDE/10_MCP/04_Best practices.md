# Mejores prácticas de MCP

> **Fuente:** [kiro.dev/docs/mcp/security/](https://kiro.dev/docs/mcp/security/)

---

## Configuración segura

### Protección de claves y tokens API

1. **Nunca comités** archivos de configuración con tokens sensibles a control de versiones
2. Crear tokens con **permisos mínimos** necesarios para el servidor MCP (ej. usa tokens de acceso personal de grano fino para GitHub en lugar de tokens clásicos)
3. Limitá el alcance de acceso solo a los repositorios o recursos necesarios
4. **Rotá regularmente** las claves API y tokens usados en la configuración
5. Usá **variables de entorno** siempre que sea posible en lugar de codificar valores

### Ejemplo: uso de variables de entorno

En lugar de codificar tokens:

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

Configura la variable de entorno en tu shell:

```bash
export GITHUB_TOKEN=your-token-value
```

### Variables de entorno aprobadas

Por seguridad, Kiro solo expande variables de entorno **explícitamente aprobadas**. Cuando agrega o modifica una configuración MCP con variables no aprobadas, Kiro muestra una ventana emergente de advertencia.

Para gestionar las variables aprobadas:
1. Configuración de Abrí Kiro
2. Buscá **"Mcp Approved Env Vars"**
3. Agrega las variables que quieras permitir

### Permisos del archivo de configuración

Restringí el acceso a tus archivos de configuración MCP:

```golpecito
# Configuración a nivel de usuario
chmod 600 ~/.kiro/settings/mcp.json

# Configuración a nivel del espacio de trabajo
chmod 600 .kiro/settings/mcp.json
```

---

## Uso seguro de herramientas

### Proceso de aprobación de herramientas

1. Revisá cada solicitud de herramienta cuidadosamente antes de aprobar
2. Verificá los parámetros que se pasan al herramienta
3. Entendé qué va a hacer la herramienta antes de aprobar
4. Denegá cualquier solicitud sospechosa que no coincida con tu tarea actual

### Pautas de aprobación automática

Solo aprobará automáticamente las herramientas que:
1. No tienen acceso de escritura a sistemas sensibles
2. Provienen de fuentes de confianza con código verificado
3. Son de uso frecuente en tu flujo de trabajo
4. Tienen alcance limitado de acceso

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

## Aislamiento del espacio de trabajo

### Uso de configuraciones a nivel de espacio de trabajo

Para proyectos con diferentes requisitos de seguridad, use configuraciones a nivel de espacio de trabajo (`.kiro/settings/mcp.json`) en lugar de la configuración global del usuario:

- Limitá los servidores MCP disponibles por proyecto
- Configurará permisos específicos para el espacio de trabajo
- Evitará exponer servidores de producción en proyectos de desarrollo.

---

## Monitoreo y Auditoría

### Comprobación de registros de MCP

Revise periódicamente los registros MCP para monitorear la actividad del servidor:

1. Abrí el panel de Kiro
2. Seleccione la pestaña **Salida**
3. Elegí **"Kiro - MCP Logs"** del menú desplegable

### Uso de la herramienta de auditoría

Periódicamente revisá qué herramientas ha aprobado:

1. Verifica tu configuración MCP para herramientas aprobadas automáticamente
2. Revisá los logs MCP para patrones de uso
3. Monitoreá la actividad del servidor en busca de comportamiento inesperado
4. Elimina la aprobación automática de herramientas que ya no usás frecuentemente

---

## Respondiendo a incidentes de seguridad

Si sospecha que un servidor MCP fue confirmado o está actuando de forma inesperada:

1. **Deshabilitar el servidor** inmediatamente: `"disabled": true` en la configuración
2. **Revocar tokens** comprometidos desde la plataforma correspondiente (GitHub, AWS, etc.)
3. **Revisar logs** para entender el alcance del problema
4. **Rotar credenciales** antes de rehabilitar el servidor

---

## Medidas de seguridad adicionales

### Seguridad de la red

- Conectar solo a servidores remotos con HTTPS
- Verifica certificados SSL de terminales remotos
- Considerá usar un proxy corporativo para servidores remotos en entornos empresariales

### Seguridad del sistema

- Mantené actualizado los paquetes npm/uvx de los servidores MCP
- Revise los registros de cambios de servidores MCP antes de actualizar
- Ejecutá servidores MCP con permisos mínimos del sistema operativo