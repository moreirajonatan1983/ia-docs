# Knowledge Management

> **Source:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#knowledge-management)

> ⚠️ **Feature experimental** — puede cambiar en futuras versiones.

---

## Overview

Knowledge Management habilita almacenamiento y recuperación de contexto persistente a través de sesiones de chat, con capacidades de **búsqueda semántica**.

**Habilitar:**
```bash
kiro-cli settings chat.enableKnowledge true
```

**Comando:** `/knowledge`

---

## Features

- Almacenamiento de archivos, directorios y contenido de texto
- Búsqueda semántica para mejor recuperación de contexto
- Base de conocimiento persistente entre sesiones
- Aislamiento de conocimiento por agente

---

## Using Knowledge Management

```
/knowledge add ./docs          # Indexar directorio
/knowledge add ./README.md     # Indexar archivo específico
/knowledge search "auth flow"  # Búsqueda semántica
/knowledge list                # Ver todo el conocimiento indexado
/knowledge delete <id>         # Eliminar un item
```

---

## Integration with Custom Agents

Podés usar knowledge bases en los recursos de un agente:

```json
{
  "resources": [{
    "type": "knowledgeBase",
    "source": "file://./docs",
    "name": "ProjectDocs",
    "description": "Project documentation",
    "indexType": "best",
    "autoUpdate": true
  }]
}
```

| Campo | Opciones | Default |
|---|---|---|
| `indexType` | `"best"` (más preciso) / `"fast"` (más rápido) | `"best"` |
| `autoUpdate` | `true` / `false` | `false` |

---

## Learn More

- [Experimental features overview →](https://kiro.dev/docs/cli/experimental/)
- [Full Knowledge Management docs →](https://kiro.dev/docs/cli/experimental/knowledge-management)