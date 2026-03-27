# Context Management

> **Source:** [kiro.dev/docs/cli/chat/context/](https://kiro.dev/docs/cli/chat/context/)

---

## Choosing the Right Context Approach

| Scenario | Approach |
|---|---|
| Essential project files (README, configs, standards) | **Agent Resources** |
| Large codebases or documentation sets | **Knowledge Bases** |
| Temporary files for current task | **Session Context** |

---

## Managing Context

### Persistent Context via Agent Resources

The recommended way to configure context is through the `resources` field in your agent config. This creates persistent context available every session.

```json
{
  "name": "my-agent",
  "description": "My development agent",
  "resources": [
    "file://README.md",
    "file://docs/**/*.md",
    "file://src/config.py"
  ]
}
```

**Resource URI schemes:**
- `file://` — Files loaded directly into context at startup
- `skill://` — Skills with metadata loaded at startup, full content on demand
- `knowledgeBase` — Indexed content searched on demand (configured as objects)

### Temporary Session Context

Add files to the current session only with `/context add`:

```
> /context add README.md
Added 1 path(s) to context.

> /context add docs/*.md
Added 3 path(s) to context.
```

⚠️ Session context is **not persistent** — not available in new sessions.

### Knowledge Bases (for large datasets)

For large codebases or documentation that would exceed context window limits:

```bash
kiro-cli settings chat.enableKnowledge true
```

```
> /knowledge add /path/to/large-codebase --include "/*.py" --exclude "node_modules/"
```

Knowledge bases are searched on-demand when relevant — ideal for large reference materials.

### Conversation Compaction

Compaction summarizes older messages to free up context window space.

- **Manual:** `/compact`
- **Automatic:** Triggers when context window overflows

After compaction, a new session is created. Resume the original via `/chat resume`.

### Viewing Context Usage

```
> /context show
Current context window (5.9% used)
  Context files    0.9%
  Tools            0.5%
  Kiro responses   0.7%
  Your prompts     3.8%
```

---

## Removing Context

Use `/context remove <path>` to remove specific files from the current session context.

---

## Best Practices

- **Context file organization** — Group related files; use glob patterns for directories
- **Performance** — Avoid loading large binary or auto-generated files (node_modules, dist, build)
- **Security** — Never add files containing secrets or credentials to agent resources