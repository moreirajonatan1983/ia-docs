# Environment Variables — Agent Sandbox

> **Source:** [kiro.dev/docs/autonomous-agent/sandbox/environment-variables/](https://kiro.dev/docs/autonomous-agent/sandbox/environment-variables/)

---

## Environment Variables

Configurá variables de entorno que estarán disponibles para el agente durante la ejecución de tareas. Son útiles para **valores de configuración que no son sensibles**.

Las variables de entorno se configuran desde [app.kiro.dev/agent/settings](https://app.kiro.dev/agent/settings) bajo **Sandbox → Environment Variables**.

---

## Secrets

Gestioná credenciales sensibles y API keys de forma segura en el sandbox.

**Características:**
- Los secrets están **cifrados en reposo**
- Se exponen como variables de entorno en el sandbox aislado durante la ejecución de tareas
- Solo se descifran dentro del entorno aislado

> ⚠️ **Advertencia de seguridad:** El agente puede exfiltrar estos secrets a través de cambios de código, logs, o requests externos. Solo proporcioná los secrets necesarios para la tarea y solo usá el agente con repositorios de confianza.

---

## Duplicate Keys

Si la misma key existe tanto en environment variables como en secrets, **el valor de la environment variable tiene precedencia**.

---

## Using Variables in MCP Configuration

Podés referenciar variables de entorno y secrets en tu configuración MCP usando la sintaxis `${key_name}`:

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

Los valores se resuelven cuando el sandbox inicia.

---

## Related

- [MCP in Sandbox →](./03_MCP.md)
- [Internet Access →](./01_Internet%20Access.md)