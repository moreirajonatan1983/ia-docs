# 🎯 Kiro Cheat Sheet

Hoja de referencia rápida de todos los atajos, comandos clave y configuraciones maestras de la suite Kiro, agrupadas por producto.

---

## 🛠 01. Kiro IDE (Editor Extension)

### ⌨️ Atajos Básicos de Teclado
| Atajo (Mac/Windows) | Acción Principal |
|---------------------|--------------------------------|
| `Cmd/Ctrl + L`      | Abrir el panel de chat contextual. |
| `Cmd/Ctrl + K`      | Generar código (Edit / In-line generation). |
| `Cmd/Ctrl + Shift + K` | Abrir barra de subagentes y herramientas. |
| `Cmd/Ctrl + Espacio`| Forzar autocompletado inteligente (Intellisense). |

### 🛠 Comandos de Chat (Slash Commands)
*Tipeá un `/` (barra oblicua) dentro de cualquier prompt en Kiro IDE para activar funciones rápidas:*
- `/explain` → Explica línea por línea el bloque de código seleccionado.
- `/fix` → Busca vulnerabilidades lógicas o bugs en el fragmento o archivo y re-escribe el método.
- `/doc` → Documenta el código automáticamente con estándares de estilo (JSDoc, Docstring).
- `/tests` → Genera tests unitarios automáticos cubriendo los flujos principales del componente.
- `/ask` (Nuevo) → Realiza preguntas conceptuales abstractas sin involucrar modificaciones de código base.

---

## 💻 02. Kiro CLI

### ⚡ Comandos Nativos de Terminal
- `kiro init` → Inicia configuración inicial en un nuevo proyecto. Genera un `.kiro/config.yml`.
- `kiro chat` → Abre la TUI interactiva para conversar en la terminal (con soporte para variables del sistema).
- `kiro delegate [tarea] --auto` → Delega un trabajo a la IA permitiendo que escriba y modifique el FS sin consultar cada paso.
- `kiro mcp add [tool]` → Instala una herramienta MCP al entorno local para mejorar el contexto de la CLI.
- `kiro check [target]` → Escanea vulnerabilidades e incompatibilidades en el path especificado.

### ⚙️ Parámetros Avanzados (`kiro chat`)
- `--context=full` → Inyecta toda la estructura de árbol pre-definida omitiendo el límite de la ventana.
- `--model=gpt-4` → Permite sobreescribir temporalmente el LLM por defecto.
- `--temp=0.x` → Control de temperatura para tareas rigurosas (0) o creativas (0.9).

---

## 🤖 03. Kiro Autonomous Agent

### 🔌 Integración con GitHub (CI/CD)
El agente autónomo "dialoga" con GitHub a través de menciones o etiquetas de incidencias. No necesita TUI.

* **Invocar al agente en Git:**
  Crear un *Issue* en GitHub y agregarle el tag `kiro-agent`. Alternativamente, escribir `@kiro-bot` en cualquier comentario de PR.
* **Auto-Merge y Testeos:**
  El Sandbox del agente es capaz de clonar, probar y mandar Pull Requests finalizados con las reparaciones o *features* listadas, requiriendo solamente tu validación de revisión de código (Review).

### 🛡 MCP & Variables Aisladas en Sandbox
Para darle Powers o llaves de API al agente sin que tu entorno las exponga, declararlas en el panel de configuración alojado en *app.kiro.dev/agent* dentro de:
- `Secure Environment Variables`
- `External Actions Access` (APIs Rest delegadas).
