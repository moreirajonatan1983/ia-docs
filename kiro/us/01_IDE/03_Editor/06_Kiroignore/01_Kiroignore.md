# Kiroignore

> **Source:** [kiro.dev/docs/editor/kiroignore/](https://kiro.dev/docs/editor/kiroignore/)

---

`.kiroignore` uses gitignore-style patterns to control which files Kiro can access. This gives you precise control over what the AI agent can read and interact with in your project.

---

## Why Use .kiroignore?

| Reason | Description |
|---|---|
| **Security** | Prevent Kiro from accessing files containing credentials, API keys, or other sensitive data |
| **Privacy** | Exclude confidential information from AI interactions |
| **Compliance** | Ensure Kiro doesn't access files that shouldn't be shared with external services |
| **Focus** | Keep Kiro's context relevant by excluding large files or build artifacts |

---

## Setting Up Workspace Ignore

To exclude files in a specific project:

1. Create a `.kiroignore` file in your project root (or any subdirectory)
2. Add patterns for files you want to exclude:

```
# Secrets and credentials
.env
.env.*
!.env.example
*.pem
*.key

# Private directories
secrets/
private/
```

3. Open **Settings** (`Cmd+,` on Mac or `Ctrl+,` on Windows/Linux)
4. Search for **Agent Ignore Files** (setting: `kiroAgent.agentIgnoreFiles`)
5. Add `.kiroignore` to the array

Kiro will now skip any files matching your patterns.

> **Tip:** Start with credentials and secrets — these are the highest priority files to protect. You can always expand your patterns as your project evolves.

---

### Setting Options

The `kiroAgent.agentIgnoreFiles` setting accepts an array of filenames:

- Use multiple ignore file types simultaneously: `[".gitignore", ".kiroignore"]`
- Set to `[]` to disable workspace-level ignore files

### Subdirectory Ignore Files

Like `.gitignore`, you can place `.kiroignore` files in subdirectories to override or extend patterns from parent directories. **Patterns in subdirectory ignore files take precedence** for files within that subdirectory.

---

## Global Ignore Files

Kiro automatically honors global ignore files if they exist — no configuration needed:

- `~/.kiro/settings/kiroignore` — Your global Kiro ignore patterns (applies to all projects)
- Git's global ignore file (configured via `core.excludesfile` in your git config) — only applied in git repositories

---

## Pattern Syntax

`.kiroignore` uses standard **gitignore syntax**:

| Pattern | Meaning |
|---|---|
| `file.txt` | Ignore a specific file |
| `*.log` | Ignore all files with `.log` extension |
| `folder/` | Ignore an entire directory |
| `**/temp` | Ignore `temp` in any directory |
| `!keep.txt` | Re-include a previously ignored file |

> **Note:** You cannot re-include a file if a parent directory is excluded. For example, if you ignore `secrets/`, adding `!secrets/public.txt` won't work. Use more specific patterns instead of excluding the entire directory.

---

## Examples

### Protecting API Keys and Secrets

```gitignore
# Environment files with credentials
.env
.env.local
.env.production

# Keep the template accessible
!.env.example

# Certificate and key files
*.pem
*.key
*.p12
credentials/
```

### Excluding Build Artifacts and Data Files

```gitignore
# Build outputs
dist/
build/
.next/

# Data files
*.sql
*.dump
data/exports/
```

### Team Compliance Setup

```gitignore
# Customer data directories
customer-data/
pii/

# Audit and compliance docs
compliance/internal/
audit-reports/
```

> Use `.kiroignore` when you need different rules for agent access vs. version control, or to block files that are tracked in git but shouldn't be read by Kiro.

---

## Best Practices

- **Use comments** to document why files are ignored — helpful for team members
- **Test patterns** by asking Kiro to read an ignored file — it will indicate access is blocked
- **Review patterns periodically** as your project structure evolves
- **Coordinate with your team** on global patterns for consistent behavior across workspaces