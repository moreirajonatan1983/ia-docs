# Interfaz

> **Fuente:** [kiro.dev/docs/editor/interface/](https://kiro.dev/docs/editor/interface/)

---

## Componentes de la interfaz principal

![Interfaz Kiro](https://kiro.dev/images/kiro-interface.png)

### Editor

El espacio de trabajo central donde escribes y editas código. Las características incluyen:

- Resaltado de sintaxis para múltiples idiomas.
- Números de línea e indicadores de error.
- Plegado de código para una mejor organización
- Múltiples pestañas para trabajar entre archivos
- Soporte de vista dividida para edición en paralelo

---

### Panel de chat

Puedes utilizar el panel de chat para:

- Haga preguntas sobre su código
- Solicitar generación o modificaciones de código.
- Obtenga ayuda con la depuración y la resolución de problemas
- Solicite revisiones de código y sugerencias de optimización.
- Incluir contexto con comandos `#` (por ejemplo, `#Archivo`, `#Carpeta`)
- Generar código repetitivo y plantillas.

> **Consejo:** Para mover el panel de chat al lado opuesto del IDE, vaya a **Ver > Apariencia > Mover la barra lateral principal a la derecha** en la barra de menú superior.

---

### Vistas

La barra lateral contiene varias vistas especializadas:

| Ver | Descripción |
|---|---|
| **Explorador** | Navegue por la estructura de archivos de su proyecto, consulte los indicadores de estado de Git y acceda a secciones especiales para especificaciones y servidores MCP |
| **Buscar** | Realice operaciones globales de búsqueda y reemplazo en todo su proyecto |
| **Control de fuente** | Administre operaciones de Git, vea cambios y maneje commits con [mensajes de commit generados por IA](https://kiro.dev/docs/editor/source-control) |
| **Ejecutar y depurar** | Ver variables, pilas de llamadas y gestionar puntos de interrupción durante las sesiones de depuración |
| **Extensiones** | Instalar y administrar extensiones IDE |
| **Kiro** | Una vista dedicada a funciones específicas de IA: administración de especificaciones, enlaces de agentes, dirección de agentes y servidores MCP |

---

### Barra de estado

Ubicada en la parte inferior de la interfaz, la barra de estado proporciona:

- Información del archivo actual
- Rama de Git y estado de sincronización
- Recuentos de errores y advertencias.
- Indicadores de estado del agente.

---

### Paleta de comandos

Accede rápidamente a los comandos de Kiro pulsando:
- **macOS:** `Cmd+Mayús+P`
- **Windows/Linux:** `Ctrl+Mayús+P`

Utilice la paleta de comandos para:
- Ejecutar acciones comunes
- Acceder a herramientas MCP
- Configurar ajustes
- Ejecutar hooks de agente

---

## Consejos de navegación

- Utilice [atajos de teclado](https://kiro.dev/docs/editor/keyboard-shortcuts/) para una navegación más rápida
- Aproveche la paleta de comandos para acceder rápidamente a las funciones
- Anclar archivos de uso frecuente para facilitar el acceso
- Utilice vistas divididas para comparar o hacer referencia al código
- Configurar los ajustes del espacio de trabajo para una experiencia personalizada

---

## Próximos pasos

- [Atajos de teclado →](https://kiro.dev/docs/editor/keyboard-shortcuts/)