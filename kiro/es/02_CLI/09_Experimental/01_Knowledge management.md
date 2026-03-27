# Gestión del conocimiento

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#knowledge-management)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

## Descripción general

La Gestión del Conocimiento habilita almacenamiento y recuperación de contexto persistente a través de sesiones de chat, con capacidades de **búsqueda semántica**.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableKnowledge verdadero
```

**Comando:** `/conocimiento`

---

## Características

- Almacenamiento de archivos, directorios y contenido de texto.
- Búsqueda semántica para mejor recuperación de contexto
- Base de conocimiento persistente entre sesiones.
- Aislamiento de conocimiento por agente

---

## Uso de la gestión del conocimiento

```
/knowledge add ./docs          # Indexar directorio
/knowledge add ./README.md     # Indexar archivo específico
/knowledge search "auth flow"  # Búsqueda semántica
/knowledge list                # Ver todo el conocimiento indexado
/knowledge delete <id>         # Eliminar un item
```

---

## Integración con agentes personalizados

Podés usar bases de conocimiento en los recursos de un agente:

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

| Campo | Opciones | Predeterminado |
|---|---|---|
| `tipo de índice` | `"best"` (más preciso) / `"fast"` (más rápido) | `"mejor"` |
| `actualización automática` | `verdadero` / `falso` | `falso` |

---

## Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos de gestión del conocimiento →](https://kiro.dev/docs/cli/experimental/knowledge-management)