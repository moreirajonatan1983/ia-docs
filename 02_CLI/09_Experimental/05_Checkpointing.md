# Puntos de control

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/#checkpointing)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

## Descripción general

Checkpointing habilita **instantáneas de sesión** para rastrear cambios de archivos usando comandos tipo Git. Funciona mediante un "shadow git repo" que captura el estado de los archivos.

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableCheckpoint verdadero
```

**Comando:** `/punto de control`

---

## Características

- Instantáneas de cambios de archivos en un repositorio de Shadow Git
- Listar, expandir, comparar y restaurar puntos de control
- El historial de conversación se revierte al restaurar.
- Se activa automáticamente en repositorios Git
- Manual de iniciación para directorios sin git

---

## Comandos

```bash
/checkpoint list                  # Ver todos los checkpoints
/checkpoint expand <tag>          # Ver detalles de un checkpoint
/checkpoint diff <tag1> [tag2]    # Comparar checkpoints
/checkpoint restore [<tag>]       # Restaurar al checkpoint
/checkpoint clean                 # Eliminar el shadow repo de la sesión
```

---

## Ejemplo de flujo de trabajo

```
> Implementar autenticación de usuario

Kiro hace varios cambios de archivos...

> /lista de puntos de control
CHECKPOINT-001 "Implementación de autenticación inicial" 5 archivos modificados
CHECKPOINT-002 "Middleware JWT agregado" 3 archivos modificados

> /diferencia punto de control CHECKPOINT-001 CHECKPOINT-002
# Muestra los cambios entre puntos de control.

# Si algo salió mal:
> /restaurar punto de control CHECKPOINT-001
# Restaura los archivos Y el historial de conversación
```

---

## Habilitar automáticamente en repositorios de Git

En repositorios Git, los puntos de control pueden activarse automáticamente al iniciar una sesión. Para directorios sin git, la inicialización es manual.

---

## Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)
- [Documentos completos sobre puntos de control →](https://kiro.dev/docs/cli/experimental/checkpointing)