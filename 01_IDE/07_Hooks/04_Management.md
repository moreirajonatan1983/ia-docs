# Gestión de hooks

> **Fuente:** [kiro.dev/docs/hooks/management/](https://kiro.dev/docs/hooks/management/)

---

Accedé a todos tus hooks desde la sección **Agent Hooks** en el panel de Kiro.

---

## Activar/Desactivar hooks

Activa o desactiva los hooks sin eliminarlos:

| Método | Cómo |
|---|---|
| **Alternancia rápida** | Haga clic en el ícono de ojo (👁) junto al gancho en el panel |
| **Desde la vista del gancho** | Seleccione el gancho → cambiar **Hook Enabled** en la esquina superior derecha |

---

## Editar hooks existentes

Los hooks evolucionan con tu flujo de trabajo. Actualizalos en cualquier momento:

1. Selecciona el gancho en el panel **Agent Hooks**
2. Modificá los campos: disparador, patrones de archivo, instrucciones o descripción
3. Los cambios se aplican **inmediatamente**

---

## Eliminar hooks

1. Selecciona el gancho en el panel **Agent Hooks**
2. Haga clic en **Eliminar gancho** (parte inferior de la vista)
3. Confirmá haciendo clic en **Eliminar**

> ⚠️ Esta acción **no se puede deshacer**.

---

## Ejecutar hooks de gatillo manual

Para hooks con gatillo de tipo **Manual**:

| Método | Cómo |
|---|---|
| **Ejecución rápida** | Click en el botón ▷ junto al nombre del gancho en el panel |
| **Desde la vista del gancho** | Seleccione el gancho → haga clic en **Iniciar gancho** en la esquina superior derecha |

---

## Almacenamiento de gancho

Los hooks se almacenan como archivos JSON en:

- `.kiro/hooks/` — engancha un espacio de trabajo nivelado (compartidos con el equipo vía git)
- Los hooks a nivel del espacio de trabajo son visibles para todos los colaboradores del proyecto.