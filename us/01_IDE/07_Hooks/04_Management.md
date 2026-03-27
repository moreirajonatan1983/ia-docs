# Hook Management

> **Source:** [kiro.dev/docs/hooks/management/](https://kiro.dev/docs/hooks/management/)

---

Accedé a todos tus hooks desde la sección **Agent Hooks** en el panel de Kiro.

---

## Enable / Disable Hooks

Activá o desactivá hooks sin eliminarlos:

| Método | Cómo |
|---|---|
| **Quick toggle** | Click en el ícono de ojo (👁) junto al hook en el panel |
| **Desde la vista del hook** | Seleccioná el hook → switch **Hook Enabled** en la esquina superior derecha |

---

## Edit Existing Hooks

Los hooks evolucionan con tu workflow. Actualizalos en cualquier momento:

1. Seleccioná el hook en el panel **Agent Hooks**
2. Modificá los campos: trigger, file patterns, instrucciones o descripción
3. Los cambios se aplican **inmediatamente**

---

## Delete Hooks

1. Seleccioná el hook en el panel **Agent Hooks**
2. Click en **Delete Hook** (parte inferior de la vista)
3. Confirmá haciendo click en **Delete**

> ⚠️ Esta acción **no se puede deshacer**.

---

## Run Manual Trigger Hooks

Para hooks con trigger de tipo **Manual**:

| Método | Cómo |
|---|---|
| **Quick run** | Click en el botón ▷ junto al nombre del hook en el panel |
| **Desde la vista del hook** | Seleccioná el hook → click **Start Hook** en la esquina superior derecha |

---

## Hook Storage

Los hooks se almacenan como archivos JSON en:

- `.kiro/hooks/` — hooks a nivel workspace (compartidos con el equipo vía git)
- Los hooks workspace-level son visibles para todos los colaboradores del proyecto