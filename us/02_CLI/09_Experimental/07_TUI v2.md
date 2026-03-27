# TUI v2

> **Source:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/)

> ⚠️ **Feature experimental** — puede cambiar en futuras versiones.

---

## Overview

**TUI v2** es la próxima generación de la interfaz de usuario de terminal (Text User Interface) de Kiro CLI, actualmente en desarrollo activo.

---

## Managing Experimental Features

Todas las features experimentales (incluyendo TUI v2) se gestionan con el comando `/experiment`:

```bash
# Ver menú interactivo
/experiment

# Ver estado actual de todos los experimentos
kiro-cli settings list | grep -i enable

# Habilitar features individuales
kiro-cli settings chat.enableKnowledge true
kiro-cli settings chat.enableTangentMode true
kiro-cli settings chat.enableTodoList true
kiro-cli settings chat.enableThinking true
kiro-cli settings chat.enableCheckpoint true
kiro-cli settings chat.enableContextUsageIndicator true
kiro-cli settings chat.enableDelegate true
```

---

## Context Usage Percentage

Una feature relacionada es el **indicador de uso de contexto** — muestra el porcentaje de ventana de contexto usada en el prompt:

**Habilitar:**
```bash
kiro-cli settings chat.enableContextUsageIndicator true
```

| Color | Uso |
|---|---|
| 🟢 Verde | < 50% |
| 🟡 Amarillo | 50-89% |
| 🔴 Rojo | 90-100% |

Ejemplo de prompt con indicador: `[rust-agent] 6% >`

---

## Fuzzy Search Support

Todos los comandos experimentales están disponibles en búsqueda fuzzy (`Ctrl+S`):

- `/experiment` — Gestionar features experimentales
- `/knowledge` — Knowledge base (cuando está habilitado)
- `/todo` — TODO lists (cuando está habilitado)
- `/tangent` — Tangent mode toggle (cuando está habilitado)
- `/checkpoint` — Checkpoint commands (cuando está habilitado)

---

## Best Practices

1. **Testear en entornos seguros** — Probar features experimentales en proyectos no críticos primero
2. **Dar feedback** — Reportar issues y sugerencias con `kiro issue`
3. **Mantenerse actualizado** — Revisar release notes para cambios en features experimentales
4. **Entender limitaciones** — Leer la documentación individual para conocer issues conocidos
5. **Tener backups** — Algunas features modifican archivos (checkpointing, TODO lists)

---

## Learn More

- [Experimental features overview →](https://kiro.dev/docs/cli/experimental/)