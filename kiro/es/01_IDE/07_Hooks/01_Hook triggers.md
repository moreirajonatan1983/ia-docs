# Hooks

> **Fuente:** [kiro.dev/docs/hooks/](https://kiro.dev/docs/hooks/)

---

Los enlaces de agente son activadores automatizados que ejecutan mensajes de agente predefinidos o comandos de shell cuando ocurren eventos específicos en su IDE. En lugar de solicitar manualmente tareas rutinarias, los hooks configuran respuestas automáticas a los eventos.

---

## ¿Qué son los hooks de agentes?

![Kiro Gancho](https://kiro.dev/videos/kiro-hook.mp4)

Los hooks pueden activarse en:
- Guardar, crear o eliminar archivos
- Envío de avisos del usuario y finalización del turno del agente.
- Antes o después de las invocaciones de herramientas.
- Antes o después de la ejecución de la tarea especificada
- Disparadores manuales bajo demanda

**Beneficios de los hooks de agentes:**
- Mantener una calidad de código consistente automáticamente
- Prevenir vulnerabilidades de seguridad.
- Reducir los gastos generales manuales
- Estandarizar los procesos del equipo.
- Crear ciclos de desarrollo más rápidos

---

## Cómo funcionan los hooks de agentes

El sistema de enlace de agente sigue un proceso simple de dos pasos:

1. **Detección de eventos**: el sistema monitorea eventos específicos en su IDE
2. **Acción automatizada**: cuando ocurre un evento, se ejecuta una acción (solicitud de agente o comando de shell)

---

## Configuración de enlaces de agentes

### Creando un gancho

1. Navegue a la sección **Agent Hooks** en el panel de Kiro.
2. Haga clic en el botón **+** para crear un nuevo gancho.
3. Elige cómo quieres crear el gancho:
   - **Crear un gancho manualmente**: configure un gancho a mano en un formulario
   - **Pídele a Kiro que cree un gancho**: describe un gancho usando lenguaje natural.

También puede abrir la interfaz de usuario de Hook desde la paleta de comandos:
- macOS: `Cmd + Shift + P` → `Kiro: abrir la interfaz de usuario de Kiro Hook`
- Windows/Linux: `Ctrl + Shift + P` → `Kiro: abrir la interfaz de usuario de Kiro Hook`

---

### Pídele a Kiro que cree un gancho

1. Selecciona **Pedirle a Kiro que cree un gancho**
2. Describe el flujo de trabajo del gancho en lenguaje natural.
3. Presione Entrar o haga clic en **Enviar**
4. Revise la configuración generada, ajústela si es necesario y haga clic en **Guardar enlace**

---

### Crear un gancho manualmente

1. Seleccione **Crear un enlace manualmente** para abrir el formulario del enlace.
2. Complete los campos del formulario:

| Campo | Descripción |
|---|---|
| **Título** | Un nombre corto para el anzuelo |
| **Descripción** | Qué hace el anzuelo |
| **Evento** | El tipo de activador (p. ej., Guardar archivo, Uso posterior de la herramienta, Ejecución previa a la tarea) |
| **Nombre de la herramienta** | Para hooks de uso previo/posterior a la herramienta, especifique qué herramientas deben coincidir |
| **Patrón de archivo** | Para enlaces de eventos de archivos, especifique qué archivos deben coincidir (por ejemplo, `src/**/*.tsx`) |
| **Acción** | Elija **Preguntar a Kiro** (solicitud de agente) o **Ejecutar comando** (comando de shell) |
| **Instrucciones o Comando** | El símbolo del sistema o comando de shell para ejecutar |

3. Haga clic en **Crear gancho** cuando haya terminado, o en **Borrar** para restablecer el formulario.

---

## Próximos pasos

- [Disparadores de gancho →](https://kiro.dev/docs/hooks/hook-triggers/)
- [Acciones de gancho →](https://kiro.dev/docs/hooks/hook-actions/)
- [Ejemplos →](https://kiro.dev/docs/hooks/examples/)
- [Gestión →](https://kiro.dev/docs/hooks/management/)
- [Mejores prácticas →](https://kiro.dev/docs/hooks/best-practices/)
- [Solución de problemas →](https://kiro.dev/docs/hooks/troubleshooting/)