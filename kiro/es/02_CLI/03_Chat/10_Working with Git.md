# Trabajando con Git

> **Fuente:** [kiro.dev/docs/cli/](https://kiro.dev/docs/cli/)

---

Kiro CLI puede trabajar junto a Git para tareas como revisar cambios, generar commits, analizar diferencias y gestionar ramas.

---

## Flujos de trabajo comunes de Git

### Revisar los cambios antes de comprometerlos

```bash
> Review the staged changes and suggest a commit message
> What files have been modified? Give me a summary of the changes
> Does this diff introduce any security issues?
```

### Generando mensajes de commit

Podés pedirle a Kiro que analice los cambios actuales y genere un mensaje de commit convencional:

```bash
> Generate a conventional commit message for the staged changes
```

### Analizando diferencias

```bash
> @src/auth.rs What changed in this file compared to main?
> Explain the changes in the last commit
```

---

## Uso de herramientas de comparación personalizadas

Podés configurar una herramienta de diferenciación externa para visualizar los cambios propuestos por Kiro:

```bash
kiro-cli settings chat.diffTool delta
kiro-cli settings chat.diffTool "delta --side-by-side"
```

Ver [Herramientas de diferenciación personalizadas →](./14_Custom%20diff%20tools.md) para más detalles.

---

## Consejos para flujos de trabajo de Git

- Usá `@` para referenciar archivos específicos: `> Revise @src/main.rs para detectar problemas antes de confirmar`
- Combiná con Hooks para automatizar acciones en eventos Git (pre-commit, post-merge)
- Usá el Plan Agent (`/plan`) para planificar características antes de hacer commit cambios
- El agente puede leer la salida de `git status`, `git diff`, `git log` directamente desde el terminal integrado

---

## Relacionado

- [Herramientas de diferenciación personalizadas →](./14_Custom%20diff%20tools.md)
- [Hooks →](https://kiro.dev/docs/cli/hooks/)
- [Referencias de archivos →](./05_Prompts.md#file-and-directory-references-v1260)