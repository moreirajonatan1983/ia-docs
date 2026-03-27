# Tu primer proyecto

> **Fuente:** [kiro.dev/docs/getting-started/first-project/](https://kiro.dev/docs/getting-started/first-project/)

---

Esta guía te lleva a través de las características esenciales de Kiro trabajando con un proyecto real. Vas a aprender a utilizar **archivos de Steering**, **Specs**, **Hooks** y **servidores MCP** para mejorar tu flujo de trabajo de desarrollo.

---

## Requisitos previos

Antes de comenzar, asegurate de tener:

- [Kiro instalado](https://kiro.dev/docs/getting-started/installation)
- Un proyecto con el que trabajar (ya sea un proyecto existente o uno nuevo)
- Familiaridad básica con la estructura y la tecnología de tu proyecto

---

## Abrí tu proyecto

1. **Iniciá Kiro y abrí tu proyecto:**
   - Usá **File > Open Folder** para seleccionar el directorio de tu proyecto.
   - O arrastrá y soltá la carpeta de tu proyecto en Kiro.
   - O desde la línea de comandos, ejecutá `kiro .` en el directorio de tu proyecto.

2. **Accedé al panel de Kiro:**
   - Hacé clic en el **icono del fantasmita de Kiro** en la barra de actividades (barra lateral izquierda).
   - Este panel te da acceso a todas las funciones impulsadas por inteligencia artificial de Kiro.

3. **Iniciá una sesión de chat:**
   - El panel de chat debería estar abierto por defecto.
   - Esto abre la interfaz conversacional de Kiro donde podés interactuar con la IA.

![Kiro Panel](https://kiro.dev/videos/kiro-pane.mp4)

---

## Configurá los archivos de Steering

Los archivos de Steering brindan contexto sobre tu proyecto, lo que ayuda a Kiro a comprender tu código base, convenciones y requisitos.

Para comenzar, elegí **Generate Steering Docs** en el panel de Kiro. Kiro genera automáticamente los documentos de Steering del proyecto (almacenados en `.kiro/steering/`) que guiarán el comportamiento de la herramienta. Estos contienen información sobre:

- Tu producto y su propósito.
- El stack tecnológico y los frameworks.
- La estructura y las convenciones del proyecto.

También podés crear archivos de Steering personalizados haciendo clic en el botón **+** en la sección de Steering y agregar cosas como estándares de código, flujos de trabajo y mejores prácticas del equipo. Conocé más sobre Steering [acá](https://kiro.dev/docs/steering/).

![Kiro Steering](https://kiro.dev/videos/kiro-steering.mp4)

---

## Construí funcionalidades con Specs

Los Specs transforman ideas de alto nivel en planes de implementación detallados a través de tres fases:

1. **Requisitos:** Historias de usuario con criterios de aceptación en notación EARS.
2. **Diseño:** Arquitectura técnica y enfoque de implementación de componentes.
3. **Tareas:** Pasos de implementación discretos y rastreables.

![Specs Start](https://kiro.dev/videos/specs-start.mp4)

### Creá tu primer Spec

1. **Iniciá un nuevo Spec:**
   - En tu sesión de chat, hacé clic en el botón **Spec**.
   - O elegí el botón **+** en la sección de Specs del panel de Kiro.

2. **Ingresá una descripción de la funcionalidad:**
   - Describí lo que querés hacer usando lenguaje natural.
   - Ejemplo: *"Agregar un sistema de autenticación de usuarios con funcionalidad de inicio de sesión, cierre de sesión y restablecimiento de contraseña"*

3. **Seguí el flujo de trabajo guiado:**
   - **Fase de requisitos:** Kiro te va a ayudar a estructurar tus requisitos utilizando la notación EARS.
   - **Fase de diseño:** Se documentará la arquitectura técnica y el diseño de componentes.
   - **Fase de implementación:** Se generarán tareas discretas para su ejecución.

### Ejecutá las tareas del Spec

Una vez que tu spec está completo:

1. Revisá las tareas generadas en el archivo `tasks.md`.
2. Ejecutá las tareas haciendo clic en los ítems individuales.
3. Hacé un seguimiento del progreso a medida que las tareas se actualizan automáticamente a *"In Progress"* y *"Done"*.

![Spec Task](https://kiro.dev/videos/spec-task.gif)

---

## Automatizá flujos de trabajo con Hooks

Los Agent Hooks (ganchos del agente) eliminan el trabajo manual al ejecutar automáticamente acciones predefinidas cuando:

- Se crean, guardan o eliminan archivos.
- Se activan triggers (disparadores) manuales.
- Se modifican patrones de archivos específicos.

Para empezar:

1. **Accedé a la creación de Hooks:**
   - Navegá a la sección **Agent Hooks** en el panel de Kiro.
   - Hacé clic en el botón **+** para crear un nuevo hook.

2. **Definí el comportamiento del hook:**
   - Describí lo que querés automatizar en lenguaje natural.
   - Ejemplo: *"Cuando guardo un archivo de un componente de React, creá o actualizá automáticamente su correspondiente archivo de prueba"*

3. **Configurá los ajustes del hook:**
   - **Event Type:** Elegí cuándo se activa el hook — eventos de archivos (crear, guardar, eliminar), eventos del ciclo de vida de los prompts o del agente (enviar prompt, detener agente, antes/después de usar herramientas), eventos de tareas del Spec (antes/después de la ejecución de una tarea), o disparo manual.
   - **File Pattern:** Especificá qué archivos deben activar este hook (por ejemplo, `src/**/*.tsx`).
   - **Instructions:** Definí las acciones específicas a realizar.

![Hooks](https://kiro.dev/videos/hooks.gif)

---

## Expandí capacidades con MCP

El Model Context Protocol (MCP) le permite a Kiro:

- Acceder a bases de conocimiento y documentación especializadas.
- Integrarse con APIs y servicios externos.
- Utilizar herramientas y utilidades específicas del dominio.
- Conectarse a bases de datos y servicios en la nube.

### Configurá MCP

1. Abrí el panel de Kiro haciendo clic en el ícono del fantasmita en la barra de actividades. Primero activá los MCPs y luego hacé clic en el botón de edición (el ícono del lápiz) al lado de MCP en el panel.
2. Por defecto, Kiro viene con el servidor [fetch MCP server](https://github.com/modelcontextprotocol/servers/tree/main/src/fetch) integrado en el archivo JSON. Cambialo a `disabled=false` para conectarte.
3. Alternativamente, podés agregar cualquier servidor MCP pidiéndole directamente a Kiro por chat que lo agregue, o editando el archivo JSON manualmente:

```json
{
  "mcpServers": {
    "web-search": {
      "command": "uvx",
      "args": ["mcp-server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "your-api-key-here"
      },
      "disabled": false,
      "autoApprove": ["search"]
    }
  }
}
```

### Usá las herramientas MCP

Una vez configuradas, podés utilizar las herramientas MCP de varias maneras:

- **Preguntas directas:** Hacé preguntas que aprovechen de frente las capacidades del servidor MCP.
  - Ejemplo: *"Buscá las últimas mejores prácticas de React 18"*
- **Uso explícito de la herramienta:** Referenciá herramientas MCP específicas usando el proveedor de contexto `#MCP`.
  - Ejemplo: `#[fetch] fetch Buscá en la web ejemplos sobre generic constraints en TypeScript`
- **Integración con otras funcionalidades:** Combiná tus MCPs con Hooks o Specs.
  - Ejemplo: *"Creá un hook que use el MCP de búsqueda web para encontrar documentación relevante en internet cada vez que creo un archivo de componente nuevo"*

---

## Próximos pasos

- [Probá el tutorial interactivo →](https://kiro.dev/docs/guides/learn-by-playing)
- [Aprendé más sobre Specs →](https://kiro.dev/docs/specs)
- [Sumate a nuestra comunidad de Discord →](https://discord.gg/kirodotdev)