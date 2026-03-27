# Servidores de desarrollo

> **Fuente:** [kiro.dev/docs/chat/dev-servers/](https://kiro.dev/docs/chat/dev-servers/)

---

El soporte del servidor de desarrollo permite al agente Kiro ejecutar procesos en segundo plano para acceder a comandos de larga ejecución sin bloquear tu flujo de trabajo. En lugar de manejar múltiples ventanas de terminal, podés pedirle a Kiro que lo maneje todo.

---

## Cómo funciona

<video src="https://kiro.dev/videos/start-process.mp4" controls autoplay muted loop playsinline width="100%" title="Iniciar proceso"></video>

Cuando pides a Kiro ejecutar un comando de larga ejecución, automáticamente:

1. Crea una terminal dedicada con un nombre descriptivo (ej. `"Kiro: npm run dev"`)
2. Inicia el proceso en segundo plano
3. Retorna el control inmediatamente para que puedas seguir trabajando
4. Rastrea el proceso para que puedas consultar su estado o salida en cualquier momento

Los procesos en segundo plano:
- Son visibles en tu lista de terminales
- Muestran el comando que están ejecutando
- Persistir hasta que los detengas o cierres Kiro

---

## Iniciar un servidor de desarrollo

Pedíselo en lenguaje natural:

- "Iniciar el servidor de desarrollo"
- "Ejecutar npm ejecutar reloj"
- "Iniciar el observador de compilación del paquete web"

### Reutilización de procesos

Kiro detecta cuando un proceso similar ya está corriendo y puede reutilizarlo en lugar de crear uno nuevo, evitando conflictos de puerto.

---

## Salida del proceso de monitoreo

Consultará el estado de tus procesos en cualquier momento:

- "Verificar la salida del servidor de desarrollo"
- "¿Qué muestra el proceso de vigilancia de ejecución de npm?"
- "¿Hay algún error en el observador de compilación?"

Kiro puede:
- Identificar errores de compilación y sugerir correcciones
- Confirmar que los servidores se iniciaron correctamente
- Depurar problemas analizando mensajes de error
- Monitorear el progreso de tareas largas

---

## Gestión de procesos

| Acción | Ejemplo |
|---|---|
| **Listar procesos activos** | "¿Qué procesos se están ejecutando?" |
| **Detener un proceso** | "Detener el servidor de desarrollo" |
| **Terminar todos** | "Eliminar todos los procesos en segundo plano" |

---

## Automatización con dirección

Podés configurar Kiro para verificar procesos automáticamente con reglas de dirección:

```markdown
# Development Workflow
After making code changes:
1. Always check the output of the `npm run dev` process
2. Look for compilation errors or warnings
3. If errors exist, suggest fixes before proceeding
```

---

## Combinación con diagnóstico de código

Los procesos en segundo plano funcionan junto con la herramienta de diagnósticos de Kiro:

- **Dev server / Build watcher** → captura de errores de compilación en tiempo de ejecución
- **Herramienta de diagnóstico** → detecta errores de tipo, advertencias de pelusa y problemas de análisis estático

Pedilos juntos: *"Verifique el resultado del observador de compilación y muéstreme cualquier error de TypeScript"*

---

## Casos de uso comunes

| Caso | Ejemplo |
|---|---|
| **Servidores de desarrollo** | Next.js, React, Vite dev server mientras codificas |
| **Construir observadores** | paquete web, TypeScript, esbuild en modo reloj |
| **Corredores de prueba** | Vitest, Jest en modo watch para feedback continuo |