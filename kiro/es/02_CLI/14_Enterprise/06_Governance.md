# Gobernanza

> **Fuente:** [kiro.dev/docs/cli/enterprise/governance/](https://kiro.dev/docs/cli/enterprise/governance/)

---

Como administrador, podrás controlar qué **modelos** y **servidores MCP** están disponibles para tus usuarios. Estos controles de gobernanza se gestionan desde la **Kiro Console → Configuración → Configuración compartida**.

---

## Gobernanza modelo

Por defecto, los usuarios pueden acceder a **cualquier modelo soportado por Kiro**. Podés restringir esto:

| Acción | Descripción |
|---|---|
| **Activar gestión de acceso al modelo** | Habilitar la gestión de acceso a modelos |
| **Seleccionar lista aprobada** | Elegir qué modelos pueden usar los usuarios |
| **Definir modelo por defecto** | Establecer un modelo que se aplica automáticamente a todos los clientes |

Para más detalles, ver [Modelos →](https://kiro.dev/docs/cli/enterprise/governance/model)

---

## Gobernanza del MCP

Por defecto, los usuarios pueden usar **cualquier servidor MCP** en su cliente Kiro. Podés:

| Opción | Descripción |
|---|---|
| **Deshabilitar MCP completamente** | Los usuarios no pueden usar ningún servidor MCP |
| **Lista de servidores permitidos** | Especificar una lista de servidores MCP aprobados mediante un registro MCP |

Estas políticas pueden establecerse a nivel de **organización** o sobreescribirse por **cuenta individual**.

Para más detalles, ver [Herramientas MCP →](https://kiro.dev/docs/cli/enterprise/governance/mcp)

---

## Cómo configurar

1. Abrir la **Consola Kiro** en AWS
2. Navegá a **Configuración → Configuración compartida**
3. Configurar las opciones de Model Governance o MCP Governance

---

## Controles empresariales adicionales

Desde **Configuración** también podés controlar:

| Configuración | Descripción |
|---|---|
| **Cifrado en reposo** | Cifrado de datos almacenados |
| **Referencias de código** | Control de referencias de código |
| **Seguimiento de uso** | Panel de uso de la organización |
| **Registro rápido** | Registro de avisos de usuarios |
| **Herramientas web** | Habilitar/deshabilitar `web_search` y `web_fetch` para todos los usuarios |
| **Excedentes** | Habilitar excedentes para usuarios del perfil |