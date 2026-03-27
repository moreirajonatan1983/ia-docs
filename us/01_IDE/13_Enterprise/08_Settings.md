# Enterprise Settings

> **Source:** [kiro.dev/docs/enterprise/settings/](https://kiro.dev/docs/enterprise/settings/)

---

Un administrador puede controlar los siguientes settings dentro de un **Kiro profile**.

---

## Available Settings

| Setting | Descripción | Más info |
|---|---|---|
| **Encryption at rest** | Configura el cifrado de datos en reposo | [Data protection →](https://kiro.dev/docs/privacy-and-security/data-protection#encryption-at-rest) |
| **Usage dashboard** | Visualización del uso agregado de Kiro | [View usage →](https://kiro.dev/docs/enterprise/monitor-and-track/dashboard) |
| **Per-user activity** | Reporte de actividad individual por usuario | [View activity →](https://kiro.dev/docs/enterprise/monitor-and-track/user-activity) |
| **Prompt logging** | Registro de todos los prompts de usuarios | [Logging prompts →](https://kiro.dev/docs/enterprise/monitor-and-track/prompt-logging) |
| **Overages** | Habilitá overages para todos los usuarios del profile | [Managing overages →](https://kiro.dev/docs/enterprise/subscription-management#enabling-overages-for-kiro-users) |
| **Web tools** | Controlá si los usuarios pueden usar `web_search` y `web_fetch` | Ver abajo |

---

## Web Tools Setting

Controla si los usuarios pueden usar las herramientas de acceso web (`web_search` y `web_fetch`).

**Para deshabilitar el acceso web para todos los usuarios:**

1. Abrí la **Kiro console**
2. Elegí **Settings**
3. En **Shared settings**, desactivá **Web search and web fetch tools**

> Cuando los web tools están deshabilitados, los usuarios verán una notificación en `/tools` indicando que el acceso web fue deshabilitado por su administrador.