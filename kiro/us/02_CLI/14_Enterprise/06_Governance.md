# Governance

> **Source:** [kiro.dev/docs/cli/enterprise/governance/](https://kiro.dev/docs/cli/enterprise/governance/)

---

Como administrador, podés controlar qué **modelos** y **servidores MCP** están disponibles para tus usuarios. Estos controles de gobernanza se gestionan desde la **Kiro Console → Settings → Shared settings**.

---

## Model Governance

Por defecto, los usuarios pueden acceder a **cualquier modelo soportado por Kiro**. Podés restringir esto:

| Acción | Descripción |
|---|---|
| **Activar model access management** | Habilitar la gestión de acceso a modelos |
| **Seleccionar lista aprobada** | Elegir qué modelos pueden usar los usuarios |
| **Definir modelo por defecto** | Establecer un modelo que se aplica automáticamente a todos los clientes |

Para más detalles, ver [Models →](https://kiro.dev/docs/cli/enterprise/governance/model)

---

## MCP Governance

Por defecto, los usuarios pueden usar **cualquier servidor MCP** en su cliente Kiro. Podés:

| Opción | Descripción |
|---|---|
| **Deshabilitar MCP completamente** | Los usuarios no pueden usar ningún servidor MCP |
| **Allow-list de servidores** | Especificar una lista de servidores MCP aprobados mediante un MCP registry |

Estas políticas pueden setearse a nivel de **organización** o sobreescribirse por **cuenta individual**.

Para más detalles, ver [MCP tools →](https://kiro.dev/docs/cli/enterprise/governance/mcp)

---

## How to Configure

1. Abrir la **Kiro Console** en AWS
2. Ir a **Settings → Shared settings**
3. Configurar las opciones de Model governance o MCP governance

---

## Additional Enterprise Controls

Desde **Settings** también podés controlar:

| Setting | Descripción |
|---|---|
| **Encryption at rest** | Cifrado de datos almacenados |
| **Code references** | Control de referencias de código |
| **Usage tracking** | Dashboard de uso por organización |
| **Prompt logging** | Logging de prompts de usuarios |
| **Web tools** | Habilitar/deshabilitar `web_search` y `web_fetch` para todos los usuarios |
| **Overages** | Habilitar overages para usuarios del profile |