# Subagentes

> **Fuente:** [kiro.dev/docs/cli/chat/subagents/](https://kiro.dev/docs/cli/chat/subagents/)

---

Los subagentes le permiten asignar tareas complejas a agentes especializados con seguimiento del progreso en vivo. Kiro puede generar subagentes para que trabajen de forma independiente en subtareas mientras tú monitoreas el progreso en tiempo real.

---

## Capacidades clave

- **Ejecución autónoma**: se ejecuta de forma independiente con su propio contexto
- **Seguimiento del progreso en vivo**: supervise las actualizaciones de estado en tiempo real mientras trabajan los subagentes
- **Acceso a herramientas principales**: lea archivos, ejecute comandos, escriba archivos y use herramientas MCP
- **Ejecución paralela**: ejecute varios subagentes simultáneamente para una ejecución eficiente de las tareas.
- **Agregación de resultados**: los resultados se devuelven automáticamente al agente principal cuando se completan

---

## Subagente predeterminado

Kiro incluye un subagente predeterminado que maneja tareas de propósito general. Cuando asigna una tarea a un subagente sin especificar un agente personalizado, se utiliza el subagente predeterminado.

---

## Subagentes personalizados

Puede generar subagentes utilizando sus propias configuraciones de agente:

```
> Use the backend agent to refactor the payment module
```

El subagente hereda el acceso a la herramienta y la configuración de la configuración de ese agente.

---

## Cómo funcionan los subagentes

1. **Asignación de tareas**: usted describe una tarea; Kiro determina si un subagente es apropiado
2. **Inicialización de subagente**: creado con su propio contexto y acceso a herramientas
3. **Ejecución autónoma**: realiza la tarea de forma independiente (puede hacer una pausa para la aprobación del permiso de la herramienta)
4. **Actualizaciones de progreso**: recibirás actualizaciones de progreso en vivo que muestran el trabajo actual.
5. **Devolución de resultados**: cuando se completa, los resultados se devuelven al agente principal.

---

## Disponibilidad de herramientas

| Disponible | No disponible |
|---|---|
| `read` — Leer archivos y directorios | `web_search` — Investigación web |
| `write` — Crear y editar archivos | `web_fetch` — Obtener URL |
| `shell` — Ejecutar comandos bash | `introspección` - información CLI |
| `código` — Inteligencia de código | `pensamiento` — Herramienta de razonamiento |
| Herramientas MCP | `todo_list` — Seguimiento de tareas |
| | `use_aws` — Comandos de AWS |
| | `grep` — Buscar contenido del archivo |
| | `glob` — Buscar archivos por patrón |

Si la configuración de su agente personalizado incluye herramientas no disponibles, simplemente se omiten: el agente aún funciona con las herramientas disponibles.

---

## Configuración del acceso de subagente

### Restringir agentes disponibles

En la configuración de su agente, especifique qué agentes se pueden usar como subagentes usando "allowedAgents".

### Confiar en agentes específicos

Utilice `trustedAgents` para permitir que subagentes específicos se ejecuten sin solicitudes de permiso.

### Combinando ambas configuraciones

Puede combinar `allowedAgents` y `trustedAgents` para obtener un control detallado sobre qué agentes se ejecutan automáticamente y cuáles requieren aprobación.