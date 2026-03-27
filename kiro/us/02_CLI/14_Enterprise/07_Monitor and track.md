# Monitor and Track

> **Source:** [kiro.dev/docs/cli/enterprise/](https://kiro.dev/docs/cli/enterprise/) | [kiro.dev/docs/cli/enterprise/settings/](https://kiro.dev/docs/cli/enterprise/settings/)

---

Kiro Enterprise proporciona herramientas para que los administradores monitoreen y rastreen el uso de la plataforma.

---

## Usage Dashboard

Visualizá el uso de Kiro a nivel de organización desde la **Kiro Console**:

- Créditos consumidos por período
- Usuarios activos
- Distribución de uso por tier

**Cómo acceder:**
1. Iniciar sesión en la **AWS Management Console**
2. Navegar a la **Kiro Console**
3. Ver la sección de **Usage / Dashboard**

---

## Per-User Activity

Visualizá la actividad individual de los usuarios:
- Última actividad por usuario (`Last active` column en la página de Subscriptions)
- Usuarios con estado **Pending** no tendrán datos en esta columna (no han activado su suscripción)

---

## Prompt Logging

Los administradores pueden habilitar el logging de prompts de los usuarios para auditoría y compliance.

**Para habilitar:**
1. Abrir la **Kiro Console**
2. Ir a **Settings**
3. Activar **Prompt logging**

Ver [Logging users' prompts →](https://kiro.dev/docs/cli/enterprise/monitor-and-track/prompt-logging)

---

## Web Tools Control

Los administradores pueden deshabilitar las herramientas web (`web_search` y `web_fetch`) para todos los usuarios:

1. Abrir la **Kiro Console**
2. Ir a **Settings → Shared settings**
3. Desactivar **Web search and web fetch tools**

Cuando están deshabilitadas, los usuarios ven una notificación en `/tools` indicando que el administrador deshabilitó el acceso web.

---

## Available Monitoring Controls

| Control | Descripción |
|---|---|
| **Usage Dashboard** | Uso agregado de la organización |
| **Per-user activity** | Actividad individual |
| **Prompt logging** | Auditoría de prompts |
| **Subscription statuses** | Active / Canceled / Pending por usuario |