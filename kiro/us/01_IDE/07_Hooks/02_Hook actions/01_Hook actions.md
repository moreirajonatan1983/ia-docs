# Hook Actions

> **Source:** [kiro.dev/docs/hooks/actions/](https://kiro.dev/docs/hooks/actions/)

---

Cada hook puede ejecutar uno de dos tipos de acciones cuando su trigger se activa.

---

## Agent Prompt Action

Define un prompt que se envía al agente cada vez que el hook se dispara. El agente responde y actúa sobre ese prompt igual que con un prompt enviado desde el panel de chat.

**Caso especial — PromptSubmit:** La acción se llama "Add to prompt". El prompt del hook se **agrega** al prompt del usuario, y el combinado se envía al agente.

**Cuándo usarlo:**
- Cuando querés usar lenguaje natural para instruir al agente a realizar alguna acción basada en contexto
- Para tareas que requieren razonamiento o evaluación inteligente
- Cuando el output depende del contexto actual del agente

> ⚠️ Las Agent Prompt actions **consumen créditos** ya que disparan un nuevo agent loop.

---

## Shell Command Action

Define un comando de shell que se ejecuta cada vez que el hook se dispara.

- **Exit code `0` (éxito):** El stdout se agrega al contexto del agente
- **Cualquier otro exit code:** El stderr se envía al agente con notificación de error
- **Pre Tool Use hook + error:** La invocación del tool es **bloqueada**
- **Prompt Submit hook + error:** El envío del prompt es **bloqueado**

**Timeout:** Configurable por hook. El default es **60 segundos**. Seteá `0` para deshabilitar el timeout.

**Cuándo usarlo:**
- Cuando querés ejecutar comandos específicos o acciones determinísticas
- Para tareas que no dependen del contexto actual del agente
- Para scripts de validación, linting, formateo, etc.

> ✅ Las Shell Command actions son **más rápidas** que las Agent Prompt actions y **no consumen créditos**, ya que se ejecutan localmente.

---

## Selecting an Action Type

- **Basado en contexto:** ✅ — ❌
- **Lenguaje natural:** ✅ — ❌
- **Determinístico:** ❌ — ✅
- **Consume créditos:** ✅ — ❌
- **Velocidad:** Más lento (LLM) — Más rápido (local)
| Ideal para | Revisión, análisis, generación | Linting, formateo, scripts |