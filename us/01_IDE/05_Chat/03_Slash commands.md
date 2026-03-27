# Slash Commands

> **Source:** [kiro.dev/docs/chat/slash-commands/](https://kiro.dev/docs/chat/slash-commands/)

---

Los slash commands permiten acceder rápidamente a hooks y archivos de steering directamente desde el input del chat escribiendo `/`.

---

## How It Works

1. Escribí `/` en el campo de input del chat
2. Navegá o buscá los comandos disponibles
3. Seleccioná un comando y presioná **Enter**

---

## Command Types

### Hooks

Los [Hooks](../07_Hooks/01_Hook triggers.md) con trigger de tipo **Manual** aparecen en el menú de slash commands. Al seleccionar uno, Kiro lo ejecuta inmediatamente en la sesión actual.

**Ejemplos:**
```
/sync-source-to-docs
/run-tests
/generate-changelog
```

➡️ Para agregar un hook como slash command: configurá su trigger type en **Manual**. Ver [Hook triggers →](../07_Hooks/01_Hook%20triggers.md)

---

### Steering Files

Los [archivos de Steering](../08_Steering.md) configurados con `inclusion: manual` en el frontmatter aparecen como slash commands. A diferencia del steering siempre activo (que se incluye automáticamente en toda conversación), el steering manual te permite incorporar guías específicas **solo cuando las necesitás**.

Al seleccionar uno, el contenido del archivo se agrega al contexto de tu conversación actual.

**Ejemplos:**
```
/accessibility
/code-review
/performance
/refactor
/testing
```

➡️ Para agregar un steering file como slash command, configurá en el frontmatter:

```markdown
---
inclusion: manual
---
```

Ver [Steering →](../08_Steering.md)

---

## Best Practices

- **Nombres descriptivos** — Nombres claros como `/run-e2e-tests` o `/accessibility` hacen que los comandos sean fáciles de encontrar
- **Context switching** — Creá steering files para diferentes workflows (frontend, backend, testing) y cambiá entre ellos según necesites
- **Combiná con `#` providers** — Los slash commands funcionan junto a los [context providers](./01_Autopilot.md) (`#file`, `#codebase`, etc.) para máximo control

---

## Related

- [Hooks →](../07_Hooks/01_Hook%20triggers.md)
- [Steering →](../08_Steering.md)
- [Terminal →](./04_Terminal.md)