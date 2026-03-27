# Espacios de trabajo multiraíz

> **Fuente:** [kiro.dev/docs/editor/multi-root-workspaces/](https://kiro.dev/docs/editor/multi-root-workspaces/)

---

Los espacios de trabajo de múltiples raíces le permiten trabajar con múltiples carpetas de proyectos simultáneamente en una sola ventana de Kiro. Las funciones de IA de Kiro están diseñadas para funcionar sin problemas en todas las carpetas raíz.

---

## Funcionalidad principal

Kiro resolverá las rutas de los archivos de forma inteligente en todas las carpetas raíz mientras navega y actualiza su espacio de trabajo de múltiples raíces.

**[Codebase Indexing](https://kiro.dev/docs/editor/codebase-indexing/)** y Repository Maps funcionan perfectamente en espacios de trabajo de múltiples raíces: ambos índices contienen código de todas las carpetas raíz y se puede hacer referencia a ellos en las indicaciones exactamente como en escenarios de espacios de trabajo de una sola raíz.

Al agregar un archivo usando el proveedor de contexto `#file`, si hay varios archivos con el mismo nombre en diferentes carpetas raíz, Kiro mostrará una lista de archivos coincidentes con sus rutas para que pueda seleccionar el correcto.

---

## Especificaciones

Kiro recupera todos los archivos [spec](https://kiro.dev/docs/specs/) de la subcarpeta `.kiro` en **cada** de las carpetas raíz y los muestra como una lista unificada en la sección Especificaciones del panel Kiro. El nombre de la carpeta raíz que contiene se muestra junto a cada especificación.

- Puedes pedirle a Kiro que trabaje en una especificación definida en cualquiera de las carpetas raíz.
- Al crear una nueva especificación, Kiro determinará la carpeta raíz adecuada para colocarla.

---

## Archivos de dirección

Kiro recupera todos los archivos [dirección](https://kiro.dev/docs/steering/) de la subcarpeta `.kiro` debajo de cada carpeta raíz, mostrándolos como una lista unificada en la sección **Dirección del agente** del panel de Kiro bajo el grupo *Espacio de trabajo*. El nombre de la carpeta raíz se muestra junto a cada archivo de dirección del espacio de trabajo.

| Directiva | Comportamiento |
|---|---|
| **Siempre incluido** | Los archivos de dirección siempre se cargan, independientemente de en qué carpeta raíz esté trabajando el agente |
| **Inclusión condicional** | Se carga solo si el agente está trabajando en un archivo en esa misma raíz y el archivo coincide con el patrón de inclusión |

Al crear un nuevo archivo de dirección del espacio de trabajo, se le pedirá que elija la carpeta raíz para guardarlo.

---

## Hooks

Kiro recupera todos los [hooks](https://kiro.dev/docs/hooks/) de la subcarpeta `.kiro` debajo de cada carpeta raíz, mostrándolos como una lista unificada en la sección **Agent Hooks**. El nombre de la carpeta raíz se muestra al lado de cada enlace.

> **Importante:** Los enlaces Crear archivo, Guardar archivo y Eliminar archivo se activan **solo** cuando el agente modifica archivos ubicados en la misma carpeta raíz donde se define el enlace.

Al crear un nuevo enlace, se le pedirá que elija la carpeta raíz.

---

## Servidores MCP

Kiro recupera todas las definiciones de [servidor MCP](https://kiro.dev/docs/mcp/) de la subcarpeta `.kiro` debajo de cada carpeta raíz, mostrándolas como una lista unificada en la sección **Servidores MCP**.

- Todos los servidores MCP definidos en todas las raíces se inicializan al inicio.
- Si dos carpetas raíz definen un servidor MCP con el mismo nombre, se utiliza la definición en la **última raíz de definición**.
- Los servidores se inician con la **primera carpeta raíz** como directorio de trabajo actual.

> Cuando hace clic en **Abrir configuración de MCP**, verá la configuración de MCP a nivel de usuario (global) de forma predeterminada. Haga clic en **Configuración del espacio de trabajo** para ver la configuración a nivel del espacio de trabajo. En un espacio de trabajo con múltiples raíces, se le pedirá que elija la carpeta raíz.