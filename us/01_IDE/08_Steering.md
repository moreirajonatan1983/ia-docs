# Steering

> **Source:** [kiro.dev/docs/steering/](https://kiro.dev/docs/steering/)

---

Steering files guide Kiro's AI with workspace-specific or global context through markdown documents that define your standards, architecture, and conventions — giving Kiro a persistent understanding of how your project works.

---

## What is Steering?

Steering files are markdown documents stored in `.kiro/steering/` that Kiro reads automatically during chat interactions. They provide project-specific knowledge that shapes Kiro's suggestions, code generation, and behavior.

**Key benefits:**
- Maintain consistent code quality across sessions
- Share team conventions automatically
- Reduce repetitive corrections
- Enable domain-specific expertise

---

## Steering File Scope

### Workspace Steering

Reside in `.kiro/steering/` in your workspace root. Apply only to that specific workspace. Used to inform Kiro of patterns, libraries, and standards that apply to an individual workspace.

### Global Steering

Reside in `~/.kiro/steering/` in your home directory. Apply to **all** workspaces. Used to inform Kiro of conventions that apply across all your projects.

> **Note:** In case of conflicting instructions between global and workspace steering, **workspace steering takes priority**.

### Team Steering

Global steering can distribute centralized steering files to entire teams via MDM solutions, Group Policies, or by downloading from a central repository to `~/.kiro/steering`.

---

## Foundational Steering Files

Click **Generate Steering Docs** in the Kiro panel to auto-generate three foundational files:

| File | Purpose |
|---|---|
| `product.md` | Defines your product's purpose, target users, key features, and business objectives |
| `tech.md` | Documents frameworks, libraries, development tools, and technical constraints |
| `structure.md` | Outlines file organization, naming conventions, import patterns, and architectural decisions |

These foundation files are included in every interaction by default.

---

## Creating Custom Steering Files

1. Navigate to the **Steering** section in the Kiro panel
2. Click the **+** button
3. Select the scope: **workspace** or **global**
4. Choose a descriptive filename (e.g., `api-standards.md`)
5. Write your guidance using standard markdown and natural language
6. Optionally use the **Refine** button to have Kiro improve your requirements

---

## Agents.md

Kiro supports the [AGENTS.md](https://agents.md/) standard. Add `AGENTS.md` files to `~/.kiro/steering/` or to the root folder of your workspace.

> **Note:** AGENTS.md files are **always included** and do not support inclusion modes.

---

## Inclusion Modes

Configure when steering files are loaded by adding YAML front matter at the top of the file:

### Always Included (default)
```yaml
---
inclusion: always
---
```
Loaded into every Kiro interaction. Best for: technology stack, coding conventions, security policies.

### Conditional Inclusion
```yaml
---
inclusion: fileMatch
fileMatchPattern: "components/**/*.tsx"
---
```
Included only when working with files matching the pattern. Multiple patterns:
```yaml
---
inclusion: fileMatch
fileMatchPattern: ["**/*.ts", "**/*.tsx", "**/tsconfig.*.json"]
---
```
Best for: component patterns, API design rules, testing approaches specific to certain file types.

### Manual Inclusion
```yaml
---
inclusion: manual
---
```
Include on-demand by referencing with `#steering-file-name` in chat, or via `/` slash commands. Best for: troubleshooting guides, migration procedures, or context-heavy documentation.

### Auto Inclusion
```yaml
---
inclusion: auto
name: api-design
description: REST API design patterns and conventions. Use when creating or modifying API endpoints.
---
```
Automatically included when your request matches the description. Also available as slash commands. Best for: context-heavy guidance that should only load when relevant.

---

## File References

Link to live workspace files to keep steering current:
```
#[[file:<relative_file_name>]]
```

Examples:
- `#[[file:api/openapi.yaml]]`
- `#[[file:components/ui/button.tsx]]`
- `#[[file:.env.example]]`

---

## Best Practices

- **Keep files focused** — One domain per file (API design, testing, deployment)
- **Use clear names** — `api-rest-conventions.md`, `testing-unit-patterns.md`
- **Include context** — Explain *why* decisions were made, not just what the standards are
- **Provide examples** — Use code snippets and before/after comparisons
- **Security first** — Never include API keys, passwords, or sensitive data
- **Maintain regularly** — Review during sprint planning and architecture changes; treat steering changes like code changes

---

## Common Steering File Strategies

| File | Content |
|---|---|
| `api-standards.md` | REST conventions, error response formats, authentication flows, versioning strategies |
| `testing-standards.md` | Unit test patterns, integration strategies, mocking, coverage expectations |
| `code-conventions.md` | Naming patterns, file organization, import ordering, architectural decisions |
| `security-policies.md` | Authentication requirements, data validation, input sanitization, vulnerability prevention |
| `deployment-workflow.md` | Build procedures, environment configurations, CI/CD pipeline details |