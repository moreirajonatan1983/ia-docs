# Agent Skills

> **Source:** [kiro.dev/docs/skills/](https://kiro.dev/docs/skills/)

---

Skills are portable instruction packages that follow the open [Agent Skills](https://agentskills.io) standard. They bundle instructions, scripts, and templates into reusable packages that Kiro can activate when relevant to your task.

Kiro supports the Agent Skills standard, so you can import skills from the community or other compatible AI tools, and share your own skills across the ecosystem.

---

## What are Skills?

Skills solve the tension between **too little context** (agents guess) and **too much context** (agents slow down) through **progressive disclosure**:

1. **Discovery** — At startup, Kiro loads only the name and description of each skill
2. **Activation** — When your request matches a skill's description, Kiro loads the full instructions
3. **Execution** — Kiro follows the instructions, loading scripts or reference files only as needed

This keeps context focused while giving Kiro access to extensive specialized knowledge on demand.

---

## How Skills Work

Without knowledge of your team's deployment process, your company's code review standards, or your project's data analysis pipeline, agents guess and iterate — just like you would when learning something new. Loading all this context upfront isn't practical.

Skills solve this by loading the full skill instructions only when Kiro determines your request matches a skill's purpose.

---

## Using Skills

Kiro **automatically activates skills** when your request matches a skill's description.

You can also invoke a skill directly: type `/` in the chat input to see available skills as **slash commands**. Selecting a slash command loads the full skill instructions.

View and manage skills in the **Agent Steering & Skills** section in the Kiro panel.

---

## Skill Scope

| Scope | Location | Best For |
|---|---|---|
| **Workspace** | `.kiro/skills/` in project root | Team procedures, project-specific workflows |
| **Global** | `~/.kiro/skills/` in home directory | Personal workflows, cross-project habits |

---

## Importing Skills

1. Open **Agent Steering & Skills** section in the Kiro panel
2. Click **+** and select **Import a skill**
3. Choose your source:
   - **GitHub** — Import from a public repository URL (paste the URL pointing to the skill folder or directly to the `SKILL.md` file). The URL must point to a subdirectory, not the repository root.
   - **Local folder** — Import from your filesystem

Imported skills are copied to your skills directory and work immediately.

---

## Creating a Skill

A skill is a folder containing a `SKILL.md` file:

```
my-skill/
├── SKILL.md        # Required
├── scripts/        # Optional executable code
├── references/     # Optional documentation
└── assets/         # Optional templates
```

### SKILL.md Format

```markdown
---
name: pr-review
description: Review pull requests for code quality, security issues, and test coverage. Use when reviewing PRs or preparing code for review.
---

## Review process

1. Check for security vulnerabilities
2. Verify error handling
3. Confirm test coverage
4. Review naming and structure
```

### Frontmatter Fields


- **name** (Required) — Skill identifier (used as slash command)
- **description** (Required) — Used by Kiro to decide when to activate
- **license** (No) — SPDX license identifier or reference to a bundled license file.
- **compatibility** (No) — Environment requirements (e.g., required tools, network access).
- **metadata** (No) — Additional key-value data like author or version.

See the [full specification →](https://agentskills.io/specification)

---

## How Skills Differ from Steering and Powers

- **Skills** are portable packages following an open standard. They load on-demand and can include scripts. Use for reusable workflows you want to share or import from others.
- **Steering** is Kiro-specific context that shapes agent behavior. It supports `always`, `auto`, `fileMatch`, and `manual` modes. Use for project standards and conventions.
- **Powers** bundle MCP tools with knowledge and workflows. They activate dynamically based on context. Use for integrations where you need both tools and guidance.

> For MCP integrations, [Powers](https://kiro.dev/docs/powers) are usually a better fit — they bundle tools with built-in guidance and activate automatically.

---

## Best Practices

- **Write precise descriptions** — Kiro uses the description to decide when to activate. Include specific keywords: "Review pull requests for security and test coverage" beats "helps with code review."
- **Keep SKILL.md focused** — Put detailed documentation in `references/` files. Kiro loads the full `SKILL.md` on activation.
- **Use scripts for deterministic tasks** — Validation, file generation, and API calls work better as scripts than LLM-generated code.
- **Choose the right scope** — Global for personal workflows (your review checklist), workspace for team procedures (project deployment).

---

## Related Documentation

- [Steering →](https://kiro.dev/docs/steering) — Project-specific context and standards
- [Powers →](https://kiro.dev/docs/powers) — MCP integrations with bundled knowledge
- [Agent Skills specification →](https://agentskills.io/specification)
