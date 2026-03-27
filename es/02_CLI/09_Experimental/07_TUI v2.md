# TUI v2

> **Fuente:** [kiro.dev/docs/cli/experimental/](https://kiro.dev/docs/cli/experimental/)

> ⚠️ **Función experimental** — puede cambiar en futuras versiones.

---

## Descripción general

**TUI v2** es la próxima generación de la interfaz de usuario de terminal (Text User Interface) de Kiro CLI, actualmente en desarrollo activo.

---

## Gestión de funciones experimentales

Todas las características experimentales (incluido TUI v2) se gestionan con el comando `/experiment`:

```golpecito
# Ver menú interactivo
/experimento

# Ver estado actual de todos los experimentos
lista de configuraciones de kiro-cli | grep -yo habilito

# Habilitar características individuales
configuración de kiro-cli chat.enableKnowledge verdadero
configuración de kiro-cli chat.enableTangentMode verdadero
configuración de kiro-cli chat.enableTodoList verdadero
configuración de kiro-cli chat.enablePensando verdadero
configuración de kiro-cli chat.enableCheckpoint verdadero
configuración de kiro-cli chat.enableContextUsageIndicator verdadero
configuración de kiro-cli chat.enableDelegate verdadero
```

---

## Porcentaje de uso del contexto

Una característica relacionada es el **indicador de uso de contexto** — muestra el porcentaje de ventana de contexto usado en el aviso:

**Habilitar:**
```golpecito
configuración de kiro-cli chat.enableContextUsageIndicator verdadero
```

| Color | Uso |
|---|---|
| 🟢 Verde | < 50% |
| 🟡 Amarillo | 50-89% |
| 🔴Rojo | 90-100% |

Ejemplo de indicador con indicador: `[rust-agent] 6% >`

---

## Soporte de búsqueda difusa

Todos los comandos experimentales están disponibles en búsqueda difusa (`Ctrl+S`):

- `/experiment` — Gestionar características experimentales
- `/knowledge` — Base de conocimientos (cuando está habilitado)
- `/todo` — Listas TODO (cuando está habilitado)
- `/tangent` — Alternar modo tangente (cuando está habilitado)
- `/checkpoint` — Comandos de punto de control (cuando está habilitado)

---

## Mejores prácticas

1. **Tesear en entornos seguros** — Probar características experimentales en proyectos no críticos primero
2. **Dar feedback** — Reportar problemas y sugerencias con `kiro issues`
3. **Mantenerse actualizado** — Revisar notas de la versión para cambios en características experimentales
4. **Entender limitaciones** — Leer la documentación individual para conocer temas conocidos
5. **Tener copias de seguridad** — Algunas características modifican archivos (puntos de control, listas de TODO)

---

## Más información

- [Descripción general de las funciones experimentales →](https://kiro.dev/docs/cli/experimental/)