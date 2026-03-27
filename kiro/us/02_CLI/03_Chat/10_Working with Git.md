# Working with Git

> **Source:** [kiro.dev/docs/cli/](https://kiro.dev/docs/cli/)

---

Kiro CLI puede trabajar junto a Git para tareas como revisar cambios, generar commits, analizar diffs y gestionar branches.

---

## Common Git Workflows

### Reviewing Changes Before Committing

```bash
> Review the staged changes and suggest a commit message
> What files have been modified? Give me a summary of the changes
> Does this diff introduce any security issues?
```

### Generating Commit Messages

Podés pedirle a Kiro que analice los cambios actuales y genere un mensaje de commit convencional:

```bash
> Generate a conventional commit message for the staged changes
```

### Analyzing Diffs

```bash
> @src/auth.rs What changed in this file compared to main?
> Explain the changes in the last commit
```

---

## Using Custom Diff Tools

Podés configurar una herramienta de diff externa para visualizar los cambios propuestos por Kiro:

```bash
kiro-cli settings chat.diffTool delta
kiro-cli settings chat.diffTool "delta --side-by-side"
```

Ver [Custom Diff Tools →](./14_Custom%20diff%20tools.md) para más detalles.

---

## Tips for Git Workflows

- Usá `@` para referenciar archivos específicos: `> Review @src/main.rs for issues before committing`
- Combiná con Hooks para automatizar acciones en eventos Git (pre-commit, post-merge)
- Usá el Plan Agent (`/plan`) para planificar features antes de commitear cambios
- El agente puede leer el output de `git status`, `git diff`, `git log` directamente desde el terminal integrado

---

## Related

- [Custom Diff Tools →](./14_Custom%20diff%20tools.md)
- [Hooks →](https://kiro.dev/docs/cli/hooks/)
- [File References →](./05_Prompts.md#file-and-directory-references-v1260)