# Agente de ayuda

> **Fuente:** [kiro.dev/docs/cli/chat/help-agent/](https://kiro.dev/docs/cli/chat/help-agent/)

---

El **Agente de ayuda** es un agente integrado que responde preguntas sobre las características de Kiro CLI usando la documentación oficial.

---

## Inicio rápido

```golpecito
# Cambiar al Agente de Ayuda
> /ayuda

# Hacer una pregunta directamente
> /ayuda ¿Cómo configuro los servidores MCP?

# Listado clásico de comandos (heredado)
> /ayuda --legado
```

Al activarse:
```
✔ Cambiado a agente: kiro_help
[ayuda] >
```

---

## Lo que puedes preguntar

El Agente de Ayuda tiene acceso a la documentación completa de Kiro CLI:

| Categoría | Ejemplos |
|---|---|
| **Comandos** | Comandos de barra diagonal (`/chat`, `/agent`, `/context`) y comandos CLI (`kiro-cli chat`, `kiro-cli settings`) |
| **Herramientas** | Herramientas integradas: `fs_read`, `code`, `grep`, `glob` |
| **Configuración** | Cualquier configuración disponible vía `kiro-cli settings` |
| **Características** | Modo tangente, Hooks, MCP, Inteligencia de código, Subagentes |
| **Atajos** | Atajos de teclado y cómo usarlos |

---

## Creando configuración

El Agente de Ayuda puede crear y modificar archivos en directorios `.kiro/`:

```
[help] > Create an agent for writing tests
✔ Created .kiro/agents/test-writer.yaml
I've created a test-writing agent. Switch with: /agent swap test-writer
```

Puede crear:
- Agentes en `.kiro/agents/`
- Indicaciones en `.kiro/prompts/`
- Configuraciones LSP en `.kiro/`

---

## Ejemplos

### Preguntar sobre un comando
```
[ayuda] > ¿Cómo guardo una conversación?
Utilice `/chat save` para guardar su conversación actual:
  /guardar chat ~/mi-sesión.json
Las conversaciones guardadas se pueden cargar más tarde con /chat load.
```

### Pregunte acerca de una herramienta
```
[ayuda] > ¿Qué hace la herramienta de código?
La herramienta de código proporciona inteligencia de código:
• search_symbols: busca definiciones de símbolos por nombre
• lookup_symbols: obtiene detalles de símbolos específicos
• get_document_symbols: enumera todos los símbolos en un archivo
• Pattern_search: búsqueda estructural basada en AST
```

### Preguntar sobre la configuración
```
[ayuda] > ¿Cómo habilito el modo tangente?
Habilite el modo tangente con:
  configuración de kiro-cli chat.enableTangentMode verdadero
O use /tangent durante una sesión de chat para alternarlo.
```

---

## Volviendo a su agente anterior

Ejecutá `/help` de nuevo mientras estés en el Help Agent para volver al agente anterior:

```
[help] > /help
✔ Switched to agent: kiro_default
```

O usamos `/agent swap <nombre>` para cambiar a un agente específico.

---

## Relacionado

- [Comandos de barra diagonal →] (https://kiro.dev/docs/cli/reference/slash-commands)
- [Agentes personalizados →](https://kiro.dev/docs/cli/custom-agents)
- [Referencia de configuración →](https://kiro.dev/docs/cli/reference/settings)