# Tu primer proyecto

> **Fuente:** [kiro.dev/docs/getting-started/first-project/](https://kiro.dev/docs/getting-started/first-project/)

---

Esta guía lo guía a través de las características esenciales de Kiro trabajando con un proyecto real. Aprenderá a utilizar **archivos de Steering**, **especificaciones**, **hooks** y **servidores MCP** para mejorar su flujo de trabajo de desarrollo.

---

## Requisitos previos

Antes de comenzar, asegúrese de tener:

- [Kiro instalado](https://kiro.dev/docs/getting-started/installation)
- Un proyecto con el que trabajar (ya sea un proyecto existente o uno nuevo)
- Familiaridad básica con la estructura y la tecnología de su proyecto.

---

## Abre tu proyecto

1. **Inicia Kiro** y abre tu proyecto:
   - Utilice **Archivo > Abrir carpeta** para seleccionar el directorio de su proyecto
   - O arrastra y suelta la carpeta de tu proyecto en Kiro
   - O vaya a la línea de comando y ejecute `kiro.` desde el directorio de su proyecto

2. **Accede al Panel Kiro:**
   - Haz clic en el **icono de Kiro Ghost** en la barra de actividades (barra lateral izquierda)
   - Este panel proporciona acceso a todas las funciones impulsadas por la IA de Kiro.

3. **Iniciar una sesión de chat:**
   - El panel de chat debería estar abierto de forma predeterminada.
   - Esto abre la interfaz conversacional de Kiro donde puedes interactuar con la IA.

<video src="https://kiro.dev/videos/kiro-pane.mp4" controls autoplay muted loop playsinline width="100%" title="Kiro Panel"></video>

---

## Configurar archivos de Steering

Los archivos de Steering brindan contexto sobre su proyecto, lo que ayuda a Kiro a comprender su código base, convenciones y requisitos.

Para comenzar, elija **Generar documentos de Steering** en el panel Kiro. Kiro genera documentos de Steering del proyecto almacenados en `.kiro/steering/` que guían el comportamiento de Kiro.

Contienen información sobre:

- Su producto y su propósito
- Pila técnica y marcos.
- Estructura y convenciones del proyecto.

También puede crear archivos de Steering personalizados haciendo clic en el botón **+** en la sección de dirección y agregar cosas como estándares de codificación, flujos de trabajo y mejores prácticas del equipo. [Más información sobre la dirección aquí →](https://kiro.dev/docs/steering/)

<video src="https://kiro.dev/videos/kiro-steering.mp4" controls autoplay muted loop playsinline width="100%" title="Dirección Kiro"></video>

---

## Construir funciones con especificaciones

Las especificaciones transforman ideas de funciones de alto nivel en planes de implementación detallados a través de tres fases:

1. **Requisitos** — Historias de usuarios con criterios de aceptación en notación EARS
2. **Diseño**: arquitectura técnica y enfoque de implementación
3. **Tareas**: pasos de implementación discretos y rastreables

<video src="https://kiro.dev/videos/specs-start.mp4" controls autoplay muted loop playsinline width="100%" title="Inicio de especificaciones"></video>

### Crea tu primera especificación

1. **Iniciar una nueva especificación:**
   - En tu sesión de chat, haz clic en el botón **Especificación**
   - O elige el botón **+** en la sección Especificaciones del panel Kiro

2. **Ingrese una descripción de la función:**
   - Describe tu característica en lenguaje natural.
   - Ejemplo: *"Agregar un sistema de autenticación de usuario con funcionalidad de inicio de sesión, cierre de sesión y restablecimiento de contraseña"*

3. **Siga el flujo de trabajo guiado:**
   - **Fase de requisitos:** Kiro le ayudará a estructurar sus requisitos utilizando la notación EARS.
   - **Fase de diseño:** Se documentará la arquitectura técnica y el diseño de componentes.
   - **Fase de implementación:** Se generarán tareas discretas para su ejecución.

### Ejecutar tareas específicas

![Tarea específica](https://kiro.dev/videos/spec-task.gif)

Una vez que su especificación esté completa:

1. Revise **Tareas generadas** en el archivo `tasks.md`
2. **Ejecutar tareas** haciendo clic en elementos de tareas individuales
3. **Seguimiento del progreso** a medida que las tareas se actualizan automáticamente a *"En curso"* y *"Listo"*

![Ejecutar tareas específicas](https://kiro.dev/videos/spec-task.gif)

---

## Automatizar flujos de trabajo con hooks

![Hooks](https://kiro.dev/videos/hooks.gif)

Agent Hooks elimina el trabajo manual al ejecutar automáticamente acciones predefinidas cuando:

- Los archivos se crean, guardan o eliminan
- Los disparadores manuales están activados.
- Se modifican patrones de archivos específicos.

**Para empezar:**

1. **Creación de gancho de acceso:**
   - Navega a la sección **Agent Hooks** en el panel de Kiro.
   - Haga clic en el botón **+** para crear un nuevo gancho.

2. **Definir comportamiento del gancho:**
   - Describe lo que quieres automatizar en lenguaje natural.
   - Ejemplo: *"Cuando guardo un archivo de componente de React, creo o actualizo automáticamente su archivo de prueba correspondiente"*

3. **Configurar ajustes de enlace:**
   - **Tipo de evento:** Elija cuándo se activa el enlace: eventos de archivos (creados, guardados, eliminados), eventos de ciclo de vida del agente y avisos (envío rápido, detención del agente, uso previo y posterior a la herramienta), eventos de tareas específicas (ejecución previa y posterior a la tarea) o activación manual
   - **Patrón de archivo:** Especifique qué archivos deben activar el enlace (por ejemplo, `src/**/*.tsx`)
   - **Instrucciones:** Definir las acciones específicas a realizar

![Automatizar flujos de trabajo con hooks](https://kiro.dev/videos/hooks.gif)

---

## Amplíe las capacidades con MCP

El Protocolo de contexto modelo (MCP) le permite a Kiro:

- Acceda a bases de conocimiento y documentación especializadas.
- Integrar con API y servicios externos
- Utilice herramientas y utilidades específicas del dominio.
- Conéctese a bases de datos y servicios en la nube.

### Configurar MCP

1. Abra el panel de Kiro haciendo clic en el icono de Kiro Ghost en la barra de actividades. Primero habilite los MCP y luego haga clic en el botón de edición (icono de lápiz) junto a MCP en el panel.

2. De forma predeterminada, Kiro se envía con [buscar servidor MCP] (https://github.com/modelcontextprotocol/servers/tree/main/src/fetch) en el archivo JSON. Voltéelo a `disabled=false` para conectarse.

3. También puedes agregar cualquier servidor MCP pidiéndole a Kiro que agregue un nuevo servidor o editando el archivo JSON directamente:

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

### Utilice herramientas MCP

Una vez configuradas, puede utilizar las herramientas MCP de varias maneras:

- **Preguntas directas**: haga preguntas que aprovechen las capacidades del servidor MCP:
  - Ejemplo: *"Buscar las últimas mejores prácticas de React 18"*

- **Uso explícito de herramientas**: haga referencia a herramientas MCP específicas con el proveedor de contexto `#MCP`:
  - Ejemplo: `#[fetch] fetch Utilice la búsqueda web para encontrar ejemplos de restricciones genéricas de TypeScript`

- **Integración con otras funciones**: combine MCP con hooks y especificaciones:
  - Ejemplo: *"Crear un enlace que utilice el MCP de búsqueda web para encontrar documentación relevante cuando creo nuevos archivos de componentes"*

---

## Próximos pasos

- [Pruebe el tutorial interactivo →](https://kiro.dev/docs/guides/learn-by-playing)
- [Más información sobre especificaciones →](https://kiro.dev/docs/specs)
- [Únete a la comunidad en Discord →](https://discord.gg/kirodotdev)