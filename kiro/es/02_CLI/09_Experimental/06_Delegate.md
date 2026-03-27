# Delegado

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#delegate)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

## Descripción general

Delegate permite lanzar y gestionar **procesos de tareas asíncronos**, ejecutando sesiones de chat de Kiro con agentes específicos en paralelo, en segundo plano.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableDelegate verdadero
```

---

## Características

- Lanzar tareas en segundo plano usando lenguaje natural.
- Ejecutar sesiones de chat paralelas con agentes específicos
- Monitorear el progreso de las tareas de forma independiente.
- Flujo de aprobación del agente para seguridad

---

## Uso

```
# Lanzar una tarea en segundo plano con lenguaje natural
> ¿Puedes crear una tarea en segundo plano para analizar el rendimiento de nuestros puntos finales API?

# El agente pide aprobación, luego ejecuta en segundo plano
✔ Lanzamiento de tarea en segundo plano: Análisis de rendimiento de API

# Verificar el estado
> Verificar el estado de mi tarea de análisis de API

# Ver resultados
> Muéstrame los resultados del análisis de antecedentes.
```

---

## Casos de uso

- **Análisis de código largo** — Ejecutar en segundo plano mientras sigues trabajando
- **Tests extensos** — Correr suites de tests sin bloquear la sesión
- **Generación de documentación** — Generar docs de Múltiples archivos en paralelo
- **Migraciones** — Tareas pesadas que llevan mucho tiempo

---

## Seguridad

El delegado incluye un **flujo de aprobación** antes de ejecutar cada tarea. Revise siempre qué va a hacer el agente antes de aprobar.

---

## Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos del delegado →](https://kiro.dev/docs/cli/experimental/delegate)