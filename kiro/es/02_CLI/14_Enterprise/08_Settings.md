# Settings

> **Fuente:** [kiro.dev/docs/cli/enterprise/settings/](https://kiro.dev/docs/cli/enterprise/settings/)

---

Un administrador puede controlar las siguientes configuraciones dentro de un **perfil de Kiro**.

---

## Configuraciones disponibles

| Configuración | Descripción |
|---|---|
| **Cifrado en reposo** | Cifrado de datos en reposo para el perfil |
| **Panel de uso** | Visualizar el uso de Kiro a nivel de organización |
| **Actividad por usuario** | Ver la actividad individual de cada usuario |
| **Registro rápido** | Registrar los avisos de los usuarios para auditoría |
| **Herramientas web** | Habilitar/deshabilitar `web_search` y `web_fetch` |
| **Organizaciones de AWS** | Integración con AWS Organizations |
| **Excedentes** | Habilitar overages para todos los usuarios del perfil |
| **Gobernanza modelo** | Controlar qué modelos pueden usar los usuarios |
| **Gobernanza del MCP** | Controlar qué servidores MCP pueden usar los usuarios |

---

## Cómo acceder a la configuración

1. Sign in en la **AWS Management Console**
2. Navegar a la **Consola Kiro**
3. Navegá a **Configuración**
4. Configurar las opciones disponibles

---

## Configuración de herramientas web

La configuración **Herramientas web** controla si los usuarios pueden usar `web_search` y `web_fetch` para buscar en la web y obtener contenido de URL.

**Para deshabilitar herramientas web:**
1. Abrir la **Consola Kiro**
2. Navegá a **Configuración → Configuración compartida**
3. Desactivar **Herramientas de búsqueda y recuperación web**

Cuando están deshabilitados, los usuarios ven una notificación en `/tools` indicando que el administrador deshabilitó el acceso web.

---

## Alcance de la configuración

Los Settings pueden configurarse a diferentes niveles:

| Nivel | Descripción |
|---|---|
| **Nivel de organización** | Aplicación a toda la organización |
| **Nivel de cuenta** | Sobreescribe la configuración de la organización para una cuenta específica |

Ver [Governance →](./06_Governance.md) para detalles sobre los controles de modelos y MCP.