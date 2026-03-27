# Interfaz

> **Fuente:** [kiro.dev/docs/editor/interface/](https://kiro.dev/docs/editor/interface/)

---

## Componentes de la interfaz principal

![Kiro Interface](https://kiro.dev/images/kiro-interface.png)

### Editor

Es tu Workspace central, donde escribís y editás tu código. Sus funcionalidades incluyen:

- Resaltado de sintaxis nativo para múltiples lenguajes.
- Números de línea e indicadores visuales de error.
- Plegado de código (`code folding`) para una mejor organización.
- Múltiples pestañas para trabajar saltando entre archivos.
- Soporte para vista dividida (*split view*) permitiéndote la edición en paralelo.

---

### Panel de Chat

Podés utilizar el panel de chat para:

- Hacer preguntas sobre tu base de código.
- Pedir que te genere código nuevo o modifique el existente.
- Obtener ayuda para debuggear (Debug) y resolver problemas.
- Solicitar revisiones de código y sugerencias avanzadas de optimización.
- Incluir contexto a la fuerza utilizando los comandos con arroba `#` (por ejemplo, `#File`, `#Folder`).
- Generar código *boilerplate* y templates de arranque.

> **Tip:** Para mover el panel del chat hacia el lado opuesto del IDE, andá a **View > Appearance > Move Primary Side Bar Right** en la barra superior del menú.

---

### Vistas (Views)

La barra lateral de Kiro (activity bar) contiene varias vistas especializadas:

| Vista | Descripción |
|---|---|
| **Explorer** | Navegá por el árbol de archivos de tu proyecto, mirá los estados y colores de Git, y accedé velozmente a las secciones donde tenés guardados tus Specs y Servidores MCP. |
| **Search** | Realizá búsquedas globales o reemplazos automáticos en todo tu proyecto. |
| **Source Control** | Administrá tus tareas de Git: revisá los diffs, controlá tus ramas y prepará tus commits usando [mensajes de commit generados por IA](https://kiro.dev/docs/editor/source-control). |
| **Run and Debug** | Inspeccioná variables, call stacks, y manipulá *breakpoints* paso a paso durante tus sesiones de Debug. |
| **Extensions** | Instalá y administrá cualquier extensión de VS Code u otro entorno. |
| **Kiro** | Una sección dedicada 100% al "cerebro": desde acá administrás Specs, Agent Hooks, el Steering principal del Agente y los Servidores MCP asociados. |

---

### Barra de estado (Status bar)

Ubicada abajo de todo en la interfaz, la barra de estado te cuenta qué está pasando:

- Detalles e información del archivo actual abierto.
- La rama de Git en la que estás y su estado de sincronización (push/pull).
- Contadores silenciosos de errores y advertencias en el proyecto.
- Indicadores visuales que te avisan el estado o disponibilidad del agente (IA).

---

### Paleta de Comandos (Command Palette)

Llegá rápidisimo a los comandos de Kiro ejecutando:
- **macOS:** `Cmd+Shift+P`
- **Windows / Linux:** `Ctrl+Shift+P`

Podés usar tu Paleta de Comandos para:
- Ejecutar comandos rutinarios y acciones comunes.
- Llamar de frente a una herramienta MCP.
- Modificar configuraciones ocultas.
- Disparar *Agent Hooks* (hooks automáticos).

---

## Consejos de navegación

- Usá los [Atajos de teclado](https://kiro.dev/docs/editor/keyboard-shortcuts/) para moverte como pez en el agua.
- Explotá la Paleta de Comandos para acceder a opciones sin tocar el mouse.
- Pineá (anclá) las pestañas de los archivos que uses más frecuente.
- Partí la pantalla con las "Vistas divididas" (*split view*) para comparar tu código o tener referencias a la vista.
- Ajustá la Configuración del Workspace de Kiro para adaptarlo 100% a tus gustos.

---

## Próximos pasos

- [Atajos de teclado →](https://kiro.dev/docs/editor/keyboard-shortcuts/)