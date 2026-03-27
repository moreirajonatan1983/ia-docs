# Settings

> **Source:** [kiro.dev/docs/cli/enterprise/settings/](https://kiro.dev/docs/cli/enterprise/settings/)

---

Un administrador puede controlar los siguientes settings dentro de un **Kiro profile**.

---

## Available Settings

| Setting | Descripción |
|---|---|
| **Encryption at rest** | Cifrado de datos en reposo para el profile |
| **Usage dashboard** | Visualizar el uso de Kiro a nivel de organización |
| **Per-user activity** | Ver la actividad individual de cada usuario |
| **Prompt logging** | Registrar los prompts de los usuarios para auditoría |
| **Web tools** | Habilitar/deshabilitar `web_search` y `web_fetch` |
| **AWS Organizations** | Integración con AWS Organizations |
| **Overages** | Habilitar overages para todos los usuarios del profile |
| **Model governance** | Controlar qué modelos pueden usar los usuarios |
| **MCP governance** | Controlar qué servidores MCP pueden usar los usuarios |

---

## How to Access Settings

1. Iniciar sesión en la **AWS Management Console**
2. Navegar a la **Kiro Console**
3. Ir a **Settings**
4. Configurar las opciones disponibles

---

## Web Tools Setting

El setting **Web Tools** controla si los usuarios pueden usar `web_search` y `web_fetch` para buscar en la web y obtener contenido de URLs.

**Para deshabilitar web tools:**
1. Abrir la **Kiro Console**
2. Ir a **Settings → Shared settings**
3. Desactivar **Web search and web fetch tools**

Cuando están deshabilitadas, los usuarios ven una notificación en `/tools` indicando que el administrador deshabilitó el acceso web.

---

## Configuration Scope

Los settings pueden configurarse a diferentes niveles:

| Nivel | Descripción |
|---|---|
| **Organization level** | Aplica a toda la organización |
| **Account level** | Sobreescribe la configuración de la organización para una cuenta específica |

Ver [Governance →](./06_Governance.md) para detalles sobre los controles de modelos y MCP.