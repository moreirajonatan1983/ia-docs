# piloto automático

> **Fuente:** [kiro.dev/docs/chat/autopilot/](https://kiro.dev/docs/chat/autopilot/)

---

El modo de piloto automático es el modo de ejecución autónoma de Kiro que permite al agente realizar cambios de código en su base de código y completar tareas complejas con una intervención mínima.

---

## ¿Qué es el modo de piloto automático?

El modo de piloto automático permite a Kiro trabajar de forma más independiente en su nombre: creando archivos, modificando código en múltiples ubicaciones, ejecutando comandos y tomando decisiones arquitectónicas sin pedir aprobación en cada paso.

---

## Cómo funciona

### Modo piloto automático *(predeterminado)*

Kiro trabaja **de forma autónoma** para completar las tareas de un extremo a otro:
- Puede crear archivos, modificar código en múltiples ubicaciones y ejecutar comandos
- Toma decisiones arquitectónicas sin pedir aprobación en cada paso.
- Mantienes el control mediante la capacidad de ver todos los cambios, revertir todo o interrumpir en cualquier momento.

### Modo supervisado

Kiro trabaja **paso a paso** con tu aprobación:
- Rinde para su aprobación después de cada turno que contiene ediciones de archivos
- Los cambios se presentan como **fragmentos individuales** (grupos lógicos de líneas relacionadas)
- Cada trozo puede ser aceptado, rechazado o discutido de forma independiente con el chat en línea
- Puede aceptar cambios a nivel de archivo o aceptar todos los cambios a la vez
- Visibilidad total de cada cambio; control detallado sobre el proceso de desarrollo

---

## Cambiar entre modos

Puede **alternar entre modos en cualquier momento** en la interfaz de chat según sus necesidades actuales y su nivel de comodidad con la tarea en cuestión.

---

## Cuándo usar cada modo

| Modo | Mejor para |
|---|---|
| **Piloto automático** | Usuarios experimentados familiarizados con Kiro, tareas repetitivas o bien definidas, proyectos en los que desea avanzar rápidamente, tareas que abarcan varios archivos o requieren varios pasos |
| **Supervisado** | Nuevos usuarios que se familiarizan con Kiro, bases de código críticas o sensibles, aprenden cómo Kiro aborda los problemas, cuándo desean revisar cuidadosamente cada cambio, trabajan con sistemas complejos o desconocidos |

---

## Funciones de gestión de cambios

### En modo piloto automático

Mantienes el control a través de varias características clave:

| Característica | Descripción |
|---|---|
| **Ver todos los cambios** | Seleccione "Ver todos los cambios" en el módulo de Chat para ver una diferencia completa de todas las modificaciones |
| **Revertir todos los cambios** | Seleccione "Revertir" para restaurar todos los archivos a su estado anterior localmente (esencialmente para deshacer todas las modificaciones de Kiro) |
| **Revertir punto de control** | Revertir a un [punto de control](https://kiro.dev/docs/chat/checkpoints): revierte tanto los cambios de archivos como las adiciones de contexto |
| **Interrumpir ejecución** | Detenga a Kiro en mitad de la ejecución en cualquier momento para recuperar el control manual |

### En modo supervisado

| Característica | Descripción |
|---|---|
| **Revisar cambios** | Kiro muestra exactamente lo que se modificó, con indicadores de cambio de línea (líneas +x -y) visibles en el chat |
| **Revisión por archivo** | Cuando se editan varios archivos, revise y acepte/rechace los cambios por archivo |
| **Revisión basada en trozos** ​​| Para modificaciones de archivos, Kiro presenta los cambios como partes individuales que pueden aceptarse, rechazarse o discutirse de forma independiente.
| **Acciones por trozo** | Aceptar, rechazar o chatear en línea sobre cualquier trozo específico |
| **Aprobación selectiva** | Aceptar algunos trozos y rechazar otros dentro del mismo archivo |
| **Aceptar todo/Rechazar todo** | Aceptar todo aplica todos los cambios pendientes y continúa; Rechazar todo revierte todo |