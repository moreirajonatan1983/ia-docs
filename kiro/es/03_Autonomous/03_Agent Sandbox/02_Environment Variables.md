# Variables de entorno: Agente Sandbox

> **Fuente:** [kiro.dev/docs/autonomous-agent/sandbox/environment-variables/](https://kiro.dev/docs/autonomous-agent/sandbox/environment-variables/)

---

## Variables de entorno

Configure variables de entorno que estarán disponibles para el agente durante la ejecución de tareas. Son útiles para **valores de configuración que no son sensibles**.

Las variables de entorno se configuran desde [app.kiro.dev/agent/settings](https://app.kiro.dev/agent/settings) bajo **Sandbox → Variables de entorno**.

---

## Secretos

Gestioná credenciales sensibles y claves API de forma segura en el sandbox.

**Características:**
- Los secretos están **cifrados en reposo**
- Se exponen como variables de entorno en el sandbox aislado durante la ejecución de tareas
- Solo se descifran dentro del entorno aislado

> ⚠️ **Advertencia de seguridad:** El agente puede exfiltrar estos secretos a través de cambios de código, registros o solicitudes externas. Solo proporcionalá los secretos necesarios para la tarea y solo usará el agente con repositorios de confianza.

---

## Claves duplicadas

Si la misma clave existe tanto en variables de entorno como en secretos, **el valor de la variable de entorno tiene precedencia**.

---

## Uso de variables en la configuración de MCP

Puedes referenciar variables de entorno y secretos en tu configuración MCP usando la sintaxis `${key_name}`:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "executable",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR_KEY": "${my_env_var_key}",
        "SECRET_KEY":  "${my_secret_key}"
      }
    }
  }
}
```

Los valores se resuelven cuando se inicia el sandbox.

---

## Relacionado

- [MCP en Sandbox →](./03_MCP.md)
- [Acceso a Internet →](./01_Internet%20Access.md)