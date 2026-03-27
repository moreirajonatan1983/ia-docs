# Gestión de hooks

> **Fuente:** [kiro.dev/docs/hooks/management/](https://kiro.dev/docs/hooks/management/)

---

Accedé a todos tus hooks desde la sección **Agent Hooks** en el panel de Kiro.

---

## Activar/Desactivar hooks

Activa o desactiva los hooks sin eliminarlos:

| Método | Cómo |
|---|---|
| **Alternancia rápida** | Hacé clic en el ícono de ojo (👁) junto al hook en el panel |
| **Desde la vista del hook** | Seleccioná el hook → cambiar **Hook Enabled** en la esquina superior derecha |

---

## Editar hooks existentes

Los hooks evolucionan con tu flujo de trabajo. Actualizalos en cualquier momento:

1. Selecciona el hook en el panel **Agent Hooks**
2. Modificá los campos: disparador, patrones de archivo, instrucciones o descripción
3. Los cambios se aplican **inmediatamente**

---

## Eliminar hooks

1. Selecciona el hook en el panel **Agent Hooks**
2. Hacé clic en **Eliminar hook** (parte inferior de la vista)
3. Confirmá haciendo clic en **Eliminar**

> ⚠️ Esta acción **no se puede deshacer**.

---

## Ejecutar hooks de gatillo manual

Para hooks con gatillo de tipo **Manual**:

| Método | Cómo |
|---|---|
| **Ejecución rápida** | Click en el botón ▷ junto al nombre del hook en el panel |
| **Desde la vista del hook** | Seleccioná el hook → haga clic en **Iniciar hook** en la esquina superior derecha |

---

## Almacenamiento de hook

Los hooks se almacenan como archivos JSON en:

- `.kiro/hooks/` — engancha un Workspace nivelado (compartidos con el equipo vía git)
- Los hooks a nivel del Workspace son visibles para todos los colaboradores del proyecto.