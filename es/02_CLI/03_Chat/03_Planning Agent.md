# Agente del plan

> **Fuente:** [kiro.dev/docs/cli/chat/planning-agent/](https://kiro.dev/docs/cli/chat/planning-agent/)

---

El **Plan Agent** transforma ideas en planos de implementación estructurados antes de escribir código. Opera en modo **solo lectura** para mantenerse enfocado en el planeamiento.

---

## Empezando

| Método | comando |
|---|---|
| **Atajo de teclado** | `Shift + Tab` — alternar entre modo plan y ejecución |
| **Comando de barra diagonal** | `/plan` |
| **Con aviso inmediato** | `/plan Crear una API REST para la autenticación de usuarios` |

Al activarse, verás el indicador `[plan]` en tu aviso y un mensaje de bienvenida.

---

## Planificar el flujo de trabajo

### 1. Recopilación de requisitos

El planificador te hace preguntas estructuradas para refinar tu idea inicial:

```
[plan] > Quiero crear una aplicación de tareas pendientes
Entiendo que quieres crear una aplicación de tareas pendientes. Déjame ayudarte a planificar esto.

[1]: ¿A qué plataforma debería apuntar esta aplicación de tareas pendientes?
a. Aplicación web b. Aplicación móvil c. Aplicación de escritorio d. Herramienta CLI

[2]: ¿Cuál es el caso de uso principal?
a. Gestión de tareas personales b. Colaboración en equipo c. Gestión de proyectos

(Utilice el chat para responder cualquier subconjunto: por ejemplo, "1=a, 2=b")
```

### 2. Investigación y análisis

El planificador explora tu código base e investiga tecnologías relevantes.

### 3. Plan de implementación

Genera un plan detallado paso a paso con objetivos claros:

```
**Plan de implementación: comando Todo CLI**

Planteamiento del problema: Agregar administración de tareas pendientes a la CLI existente.

Tarea 1: crear esquemas y modelos de base de datos
- Definir la estructura Todo con campos obligatorios
- Demostración: puede crear y consultar todos en la base de datos

Tarea 2: implementar la estructura de comandos CLI
- Agregar subcomando todo con operaciones de agregar/listar/completar
- Demostración: CLI acepta comandos de tareas pendientes y muestra ayuda
```

Cada tarea incluye: objetivos claros, guía de implementación, descripción de demostración.

### 4. Aprobación y transferencia del plan

Antes de pasar a ejecución, el planificador solicita tu aprobación:

```
[plan] > ¿Este plan se ve bien o le gustaría que ajustara algo?
> ¡Se ve genial! Implementémoslo.

¡Planificación completa! ¿Listo para salir del agente [plan]? [t/n]: sí
```

El proceso de traspaso:
1. Aprobás el plan de implementación
2. Prompt interactivo confirma el cambio al modo de ejecución
3. Transición automática al agente anterior
4. El plan completo se pasa al agente de ejecución

---

## Diseño de solo lectura

El Plan Agent opera en modo **solo lectura** para mantener el foco en el planeamiento. No modifica archivos durante la fase de planificación.

---

## Mejores prácticas

1. **Usalo para tareas complejas** — más valioso para implementaciones de múltiples pasos
2. **Respondé las preguntas con detalle** — mejora la calidad del plan
3. **Dejalo explorar** — permití que analice tu código base existente
4. **Revisá los planes** — asegurate de que el plan coincide con tus expectativas antes del traspaso
5. **Iterá** — refinará hasta que el plan sea claro

---

## Ejemplo de flujo de trabajo

```
> /plan Agregar autenticación de usuario a mi aplicación web

[plan] > Según tengo entendido: desea implementar la autenticación de usuario.

[1]: ¿Qué método de autenticación prefieres?
a. Correo electrónico/contraseña b. OAuth c. Enlaces mágicos d. Multifactor
> 1=un

[2]: ¿Cuál es tu pila tecnológica actual?
d. Otro: especifique
> 2=d, estoy usando Rust con el framework Axum

*Investigando patrones de autenticación de Axum...*
*Explorando su estructura base de código existente...*

**Plan de implementación: sistema de autenticación de usuarios**
[Plan detallado...]

¿Se ve bien este plan? > ¡Se ve perfecto!
¿Listo para salir del agente [plan]? [t/n]: sí

[predeterminado] > Implementar este plan: [Plan transferido al agente de ejecución]
```