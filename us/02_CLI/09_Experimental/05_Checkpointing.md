# Checkpointing

> **Source:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#checkpointing)

> ⚠️ **Feature experimental** — puede cambiar en futuras versiones.

---

## Overview

Checkpointing habilita **snapshots de sesión** para trackear cambios de archivos usando comandos Git-like. Funciona mediante un "shadow git repo" que captura el estado de los archivos.

**Habilitar:**
```bash
kiro-cli settings chat.enableCheckpoint true
```

**Comando:** `/checkpoint`

---

## Features

- Snapshots de cambios de archivos en un shadow git repo
- Listar, expandir, comparar y restaurar checkpoints
- El historial de conversación se revierte al restaurar
- Se activa automáticamente en repositorios Git
- Inicialización manual para directorios sin git

---

## Commands

```bash
/checkpoint list                  # Ver todos los checkpoints
/checkpoint expand <tag>          # Ver detalles de un checkpoint
/checkpoint diff <tag1> [tag2]    # Comparar checkpoints
/checkpoint restore [<tag>]       # Restaurar al checkpoint
/checkpoint clean                 # Eliminar el shadow repo de la sesión
```

---

## Example Workflow

```
> Implement user authentication

Kiro hace varios cambios de archivos...

> /checkpoint list
CHECKPOINT-001  "Initial auth implementation"  5 files changed
CHECKPOINT-002  "Added JWT middleware"          3 files changed

> /checkpoint diff CHECKPOINT-001 CHECKPOINT-002
# Muestra los cambios entre checkpoints

# Si algo salió mal:
> /checkpoint restore CHECKPOINT-001
# Restaura los archivos Y el historial de conversación
```

---

## Auto-Enable in Git Repos

En repositorios Git, los checkpoints pueden activarse automáticamente al iniciar una sesión. Para directorios sin git, la inicialización es manual.

---

## Learn More

- [Experimental features overview →](https://kiro.dev/docs/cli/experimental/)
- [Full Checkpointing docs →](https://kiro.dev/docs/cli/experimental/checkpointing)