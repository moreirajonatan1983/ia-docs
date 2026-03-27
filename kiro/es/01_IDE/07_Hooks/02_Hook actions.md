# Acciones de hook

> **Fuente:** [kiro.dev/docs/hooks/actions/](https://kiro.dev/docs/hooks/actions/)

---

Cada hook puede ejecutar uno de dos tipos de acciones cuando su disparador se activa.

---

## Acción de solicitud del agente

Defina un mensaje que se envía al agente cada vez que el hook se dispara. El agente responde y actúa sobre ese aviso igual que con un aviso enviado desde el panel de chat.

**Caso especial — PromptSubmit:** La acción se llama "Agregar al mensaje". El aviso del hook se **agrega** al aviso del usuario, y el combinado se envía al agente.

**Cuándo usarlo:**
- Cuando quieras usar lenguaje natural para instruir al agente a realizar alguna acción basada en contexto
- Para tareas que requieren razonamiento o evaluación inteligente
- Cuando la salida depende del contexto actual del agente

> ⚠️ Las acciones de Agent Prompt **consumen créditos** ya que disparan un nuevo agente loop.

---

## Acción del comando Shell

Defina un comando de shell que se ejecute cada vez que el hook se dispare.

| Resultado del comando | Comportamiento |
|---|---|
| Código de salida `0` (éxito) | El stdout se agrega al contexto del agente |
| Cualquier otro código de salida | El stderr se envía al agente con notificación de error |
| Herramienta previa Uso hook + error | La invocación de la herramienta es **bloqueada** |
| Preguntar Enviar hook + error | El envío del aviso es **bloqueado** |

**Tiempo de espera:** Configurable por hook. El valor predeterminado es **60 segundos**. Seteá `0` para deshabilitar el tiempo de espera.

**Cuándo usarlo:**
- Cuando quieras ejecutar comandos específicos o acciones determinísticas
- Para tareas que no dependen del contexto actual del agente
- Para scripts de validación, linting, formateo, etc.

> ✅ Las acciones de Shell Command son **más rápidas** que las acciones de Agent Prompt y **no consumen créditos**, ya que se ejecutan localmente.

---

## Seleccionar un tipo de acción

| Criterio | Aviso del agente | Comando Shell |
|---|---|---|
| Basado en contexto | ✅ | ❌ |
| Lenguaje natural | ✅ | ❌ |
| Determinístico | ❌ | ✅ |
| Consumir créditos | ✅ | ❌ |
| Velocidad | Más lento (LLM) | Más rápido (local) |
| Ideal para | Revisión, análisis, generación | Linting, formateo, scripts |