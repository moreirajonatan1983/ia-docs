# Configuración empresarial

> **Fuente:** [kiro.dev/docs/enterprise/settings/](https://kiro.dev/docs/enterprise/settings/)

---

Un administrador puede controlar las siguientes configuraciones dentro de un **perfil de Kiro**.

---

## Configuraciones disponibles

| Configuración | Descripción | Más información |
|---|---|---|
| **Cifrado en reposo** | Configurar el cifrado de datos en reposo | [Protección de datos →](https://kiro.dev/docs/privacy-and-security/data-protection#encryption-at-rest) |
| **Panel de uso** | Visualización del uso agregado de Kiro | [Ver uso →](https://kiro.dev/docs/enterprise/monitor-and-track/dashboard) |
| **Actividad por usuario** | Informe de actividad individual por usuario | [Ver actividad →](https://kiro.dev/docs/enterprise/monitor-and-track/user-activity) |
| **Registro rápido** | Registro de todos los avisos de usuarios | [Indicaciones de registro →](https://kiro.dev/docs/enterprise/monitor-and-track/prompt-logging) |
| **Excedentes** | Habilitá overages para todos los usuarios del perfil | [Gestión de excedentes →](https://kiro.dev/docs/enterprise/subscription-management#enabling-overages-for-kiro-users) |
| **Herramientas web** | Controlá si los usuarios pueden usar `web_search` y `web_fetch` | Ver abajo |

---

## Configuración de herramientas web

Controla si los usuarios pueden usar las herramientas de acceso web (`web_search` y `web_fetch`).

**Para deshabilitar el acceso web para todos los usuarios:**

1. Abrí la **consola Kiro**
2. Elegí **Ajustes**
3. En **Configuración compartida**, desactiva **Herramientas de búsqueda y recuperación web**

> Cuando las herramientas web están deshabilitadas, los usuarios verán una notificación en `/tools` indicando que el acceso web fue deshabilitado por su administrador.