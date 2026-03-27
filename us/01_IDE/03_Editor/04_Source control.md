# Source Control

> **Source:** [kiro.dev/docs/editor/source-control/](https://kiro.dev/docs/editor/source-control/)

---

Kiro enhances your Git workflow with AI-powered commit message generation and seamless version control integration.

---

## Commit Message Generation

![Git Commit Message](https://kiro.dev/videos/git-commit-message.mp4)

Kiro can automatically generate descriptive commit messages following the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) format by analyzing your staged changes.

### How to Generate Commit Messages

1. **Stage your changes** in the Source Control panel
2. Click the **🪄 button** next to the commit message input field
3. **Review the generated message** — Kiro analyzes your changes and creates a descriptive commit message
4. **Edit if needed** — You can modify the generated message before committing
5. **Commit your changes** using the generated or edited message

> **Tip:** You can set up a custom keyboard shortcut for `Kiro: Generate Commit Message` in your keyboard settings for faster access.

---

### Message Format

Kiro follows the **Conventional Commits** format:

```
<type>(<scope>): <subject>
- First change or addition
- Second change or improvement
- Third change if applicable
- Why this change was needed (if relevant)
```

### Conventional Commit Types

| Type | Description |
|---|---|
| `feat` | New features |
| `fix` | Bug fixes |
| `docs` | Documentation changes |
| `style` | Formatting changes |
| `refactor` | Code restructuring |
| `test` | Adding/updating tests |
| `chore` | Maintenance tasks |
| `perf` | Performance improvements |
| `ci` | CI/CD changes |

### Example

```
feat(docs): add comprehensive Source Control documentation
- Create new documentation page for Source Control features
- Update interface documentation to link to Source Control page
- Provide detailed explanation of AI-powered commit message generation
- Describe diff context provider and commit message generation process
```

---

## Git Diff Context Provider

Kiro includes a `#Git Diff` context provider that lets you reference your current uncommitted changes directly in the chat. This is useful for:

- Fixing merge conflicts
- Reviewing changes before committing
- Getting a code review on your current diff

### Example Usage

```
Hey Kiro, can you fix the merge conflicts? #Git Diff
```

---

## Troubleshooting

### Git Operations Failing

- Check your Git configuration and credentials
- Ensure you have proper permissions for the repository