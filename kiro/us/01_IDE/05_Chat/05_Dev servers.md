# Dev Servers

> **Source:** [kiro.dev/docs/chat/dev-servers/](https://kiro.dev/docs/chat/dev-servers/)

---

Dev server support permite al agente Kiro ejecutar procesos en segundo plano para acceder a comandos de larga ejecución sin bloquear tu workflow. En lugar de manejar múltiples ventanas de terminal, podés pedirle a Kiro que lo maneje todo.

---

## How It Works

![Start Process](https://kiro.dev/videos/start-process.mp4)


Cuando pedís a Kiro ejecutar un comando de larga ejecución, automáticamente:

1. Crea una terminal dedicada con un nombre descriptivo (ej. `"Kiro: npm run dev"`)
2. Inicia el proceso en segundo plano
3. Retorna el control inmediatamente para que puedas seguir trabajando
4. Rastrea el proceso para que puedas consultar su estado o salida en cualquier momento

Los procesos en segundo plano:
- Son visibles en tu lista de terminales
- Muestran el comando que están ejecutando
- Persisten hasta que los detengas o cierres Kiro

---

## Starting a Dev Server

Pedíselo en lenguaje natural:

- "Start the development server"
- "Run npm run watch"
- "Start the webpack build watcher"

### Process Reuse

Kiro detecta cuando un proceso similar ya está corriendo y puede reutilizarlo en lugar de crear uno nuevo, evitando conflictos de puerto.

---

## Monitoring Process Output

Consultá el estado de tus procesos en cualquier momento:

- "Check the output of the dev server"
- "What does the npm run watch process show?"
- "Are there any errors in the build watcher?"

Kiro puede:
- Identificar errores de compilación y sugerir fixes
- Confirmar que los servidores iniciaron correctamente
- Debuggear problemas analizando mensajes de error
- Monitorear el progreso de tareas largas

---

## Managing Processes

| Acción | Ejemplo |
|---|---|
| **Listar procesos activos** | "What processes are running?" |
| **Detener un proceso** | "Stop the development server" |
| **Terminar todos** | "Kill all background processes" |

---

## Automating with Steering

Podés configurar Kiro para chequear procesos automáticamente con steering rules:

```markdown
# Development Workflow
After making code changes:
1. Always check the output of the `npm run dev` process
2. Look for compilation errors or warnings
3. If errors exist, suggest fixes before proceeding
```

---

## Combining with Code Diagnostics

Los procesos en segundo plano funcionan junto con la herramienta de diagnósticos de Kiro:

- **Dev server / Build watcher** → captura errores de compilación en tiempo de ejecución
- **Diagnostics tool** → detecta type errors, lint warnings y problemas de análisis estático

Pedilos juntos: *"Check the build watcher output and show me any TypeScript errors"*

---

## Common Use Cases

| Caso | Ejemplo |
|---|---|
| **Development servers** | Next.js, React, Vite dev server mientras codificás |
| **Build watchers** | webpack, TypeScript, esbuild en modo watch |
| **Test runners** | Vitest, Jest en modo watch para feedback continuo |