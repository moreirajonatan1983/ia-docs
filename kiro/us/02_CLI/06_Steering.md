# Steering — Kiro CLI

> **Source:** [kiro.dev/docs/cli/steering/](https://kiro.dev/docs/cli/steering/)

---

Steering files guide Kiro's AI with project-specific context through markdown documents that define your standards, architecture, and conventions.

---

## What is Steering?

Steering files are markdown documents stored in `.kiro/steering/` that Kiro reads automatically during chat sessions. They provide project-specific knowledge that shapes Kiro's code generation and behavior.

**Key benefits:**
- Consistent code quality across sessions
- Automatic application of team conventions
- Reduced repetitive corrections
- Domain-specific expertise

---

## Steering File Scope

### Workspace Steering

Reside in `.kiro/steering/` in your workspace root. Apply only to that specific workspace.

### Global Steering

Reside in `~/.kiro/steering/` in your home directory. Apply to **all** workspaces.

> **Note:** In case of conflicting instructions, **workspace steering takes priority** over global steering.

### Team Steering

Global steering files can be distributed to entire teams via MDM solutions, Group Policies, or downloaded from a central repository to `~/.kiro/steering`.

---

## Foundational Steering Files

Create foundational steering files in `.kiro/steering/` (workspace) or `~/.kiro/steering` (global):

| File | Purpose |
|---|---|
| `product.md` | Product purpose, target users, key features, and business objectives |
| `tech.md` | Frameworks, libraries, development tools, and technical constraints |
| `structure.md` | File organization, naming conventions, import patterns, and architectural decisions |

These foundation files are included in every interaction by default.

---

## Creating Custom Steering Files

1. Create a new `.md` file in `.kiro/steering/`
2. Choose a descriptive filename (e.g., `api-standards.md`)
3. Write your guidance using standard markdown and natural language

---

## Steering with Custom Agents

When using [custom agents](https://kiro.dev/docs/cli/custom-agents/creating), steering files are **not automatically included**. Add them explicitly to the agent's `resources` configuration:

```json
{
  "resources": ["file://.kiro/steering/**/*.md"]
}
```

This glob pattern ensures all markdown files in your steering directory are loaded when using the agent.

---

## Agents.md

Kiro supports the [AGENTS.md](https://agents.md/) standard. Add `AGENTS.md` files to `~/.kiro/steering/` or to the root folder of your workspace — they are **always included** automatically.

---

## Best Practices

- **Keep files focused** — One domain per file
- **Use clear names** — `api-rest-conventions.md`, `testing-unit-patterns.md`
- **Include context** — Explain *why* decisions were made
- **Provide examples** — Use code snippets and before/after comparisons
- **Security first** — Never include API keys or sensitive data
- **Maintain regularly** — Treat steering changes like code changes

---

## Common Steering File Strategies

| File | Content |
|---|---|
| `api-standards.md` | REST conventions, error response formats, authentication flows |
| `testing-standards.md` | Unit test patterns, integration strategies, mocking, coverage |
| `code-conventions.md` | Naming patterns, file organization, architectural decisions |
| `security-policies.md` | Authentication requirements, data validation, secure coding |
| `deployment-workflow.md` | Build procedures, environment configurations, CI/CD details |