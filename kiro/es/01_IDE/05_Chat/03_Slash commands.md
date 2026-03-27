# Comandos de barra diagonal

> **Fuente:** [kiro.dev/docs/chat/slash-commands/](https://kiro.dev/docs/chat/slash-commands/)

---

Los comandos de barra diagonal permiten acceder rápidamente a hooks y archivos de Steering directamente desde la entrada del chat escribiendo `/`.

---

## Cómo funciona

1. Escribí `/` en el campo de entrada del chat
2. Navegá o buscá los comandos disponibles
3. Seleccioná un comando y presione **Entrar**

---

## Tipos de comandos

### Hooks

Los [Hooks](../07_Hooks/01_Hook triggers.md) con disparador de tipo **Manual** aparecen en el menú de comandos de barra diagonal. Al seleccionar uno, Kiro lo ejecuta inmediatamente en la sesión actual.

**Ejemplos:**
```
/sincronizar-fuente-con-docs
/ejecutar-pruebas
/generar-registro de cambios
```

➡️ Para agregar un comando de hook como barra diagonal: configure su tipo de disparador en **Manual**. Ver [Disparadores de hook →](../07_Hooks/01_Hook%20triggers.md)

---

### Archivos de Steering

Los [archivos de Steering](../08_Steering.md) configurados con `inclusion: manual` en el frontmatter aparecen como comandos de barra diagonal. A diferencia del volante siempre activo (que se incluye automáticamente en toda conversación), el volante manual te permite incorporar guías específicas **solo cuando las necesidades**.

Al seleccionar uno, el contenido del archivo se agrega al contexto de tu conversación actual.

**Ejemplos:**
```
/accesibilidad
/revisión-de-código
/rendimiento
/refactorizar
/pruebas
```

➡️ Para agregar un archivo de Steering como comando de barra diagonal, configurará en el frontmatter:

```markdown
---
inclusion: manual
---
```

Ver [Dirección →](../08_Steering.md)

---

## Mejores prácticas

- **Nombres descriptivos** — Nombres claros como `/run-e2e-tests` o `/accessibility` hacen que los comandos sean fáciles de encontrar
- **Cambio de contexto** — Creará archivos de Steering para diferentes flujos de trabajo (frontend, backend, pruebas) y cambiará entre ellos según sea necesario
- **Combiná con `#` proveedores** — Los comandos de barra diagonal funcionan junto a los [context Providers](./01_Autopilot.md) (`#file`, `#codebase`, etc.) para máximo control

---

## Relacionado

- [Hooks →](../07_Hooks/01_Hook%20triggers.md)
- [Dirección →](../08_Steering.md)
- [Terminal →](./04_Terminal.md)