# Help Agent

> **Source:** [kiro.dev/docs/cli/chat/help-agent/](https://kiro.dev/docs/cli/chat/help-agent/)

---

El **Help Agent** es un agente integrado que responde preguntas sobre las features del Kiro CLI usando la documentación oficial.

---

## Quick Start

```bash
# Cambiar al Help Agent
> /help

# Hacer una pregunta directamente
> /help How do I configure MCP servers?

# Listado clásico de comandos (legacy)
> /help --legacy
```

Al activarse:
```
✔ Switched to agent: kiro_help
[help] >
```

---

## What You Can Ask

El Help Agent tiene acceso a la documentación completa de Kiro CLI:

| Categoría | Ejemplos |
|---|---|
| **Commands** | Slash commands (`/chat`, `/agent`, `/context`) y CLI commands (`kiro-cli chat`, `kiro-cli settings`) |
| **Tools** | Herramientas integradas: `fs_read`, `code`, `grep`, `glob` |
| **Settings** | Cualquier setting disponible vía `kiro-cli settings` |
| **Features** | Tangent Mode, Hooks, MCP, Code Intelligence, Subagents |
| **Shortcuts** | Atajos de teclado y cómo usarlos |

---

## Creating Configuration

El Help Agent puede crear y modificar archivos en directorios `.kiro/`:

```
[help] > Create an agent for writing tests
✔ Created .kiro/agents/test-writer.yaml
I've created a test-writing agent. Switch with: /agent swap test-writer
```

Puede crear:
- Agents en `.kiro/agents/`
- Prompts en `.kiro/prompts/`
- LSP configs en `.kiro/`

---

## Examples

### Ask About a Command
```
[help] > How do I save a conversation?
Use `/chat save` to save your current conversation:
  /chat save ~/my-session.json
Saved conversations can be loaded later with /chat load.
```

### Ask About a Tool
```
[help] > What does the code tool do?
The code tool provides code intelligence:
• search_symbols - Find symbol definitions by name
• lookup_symbols - Get details for specific symbols
• get_document_symbols - List all symbols in a file
• pattern_search - AST-based structural search
```

### Ask About Configuration
```
[help] > How do I enable tangent mode?
Enable Tangent Mode with:
  kiro-cli settings chat.enableTangentMode true
Or use /tangent during a chat session to toggle it.
```

---

## Returning to Your Previous Agent

Ejecutá `/help` de nuevo mientras estás en el Help Agent para volver al agente anterior:

```
[help] > /help
✔ Switched to agent: kiro_default
```

O usá `/agent swap <nombre>` para cambiar a un agente específico.

---

## Related

- [Slash Commands →](https://kiro.dev/docs/cli/reference/slash-commands)
- [Custom Agents →](https://kiro.dev/docs/cli/custom-agents)
- [Settings Reference →](https://kiro.dev/docs/cli/reference/settings)