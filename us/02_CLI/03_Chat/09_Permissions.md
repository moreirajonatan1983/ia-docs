# Managing Tool Permissions

> **Source:** [kiro.dev/docs/cli/chat/permissions/](https://kiro.dev/docs/cli/chat/permissions/)

---

Kiro CLI uses a granular permission system that lets you control exactly which tools can run automatically and which require your approval each time.

---

## Tools Commands

| Command | Action |
|---|---|
| `/tools` | View permission status for all current tools |
| `/tools trust <tool>` | Trust a specific tool for the current session |
| `/tools untrust <tool>` | Untrust a specific tool for the current session |
| `/tools trust-all` | Trust all tools at once (use with caution) |
| `/tools reset` | Reset permissions to default |

```bash
$ kiro-cli chat
Kiro> /tools
Kiro> /tools trust read
Kiro> /tools untrust shell
Kiro> /tools trust-all
```

**Permission states:**
- **Trusted** — Kiro can use the tool without asking for confirmation
- **Per-request** — Kiro must ask for your confirmation each time

> ⚠️ `/tools trust-all` carries security risks. See [Using /tools trust-all safely](https://kiro.dev/docs/cli/chat/security/#using-tools-trust-all-safely).

---

## Available Tools

| Tool | Description |
|---|---|
| `read` | Read files and directories |
| `write` | Create and edit files |
| `shell` | Execute bash commands |
| `aws` | AWS CLI integration |
| `report` | Report information |

---

## Shell Command Trust Levels

When Kiro asks to run a shell command, you get a **tiered trust picker** instead of all-or-nothing:

```
Press (↑↓) to navigate (⏎) to select scope
> Full command    → git pull --rebase
  Partial command → git pull *
  Base command    → git *
  Entire Tool     → *
```

**Trust tiers (most → least restrictive):**

| Tier | Example | Covers |
|---|---|---|
| Full command | `git pull --rebase` | Only this exact command |
| Partial command | `git pull *` | Any `git pull` variant |
| Base command | `git *` | All git commands |
| Entire Tool | `*` | All shell commands |

After selecting, Kiro confirms: `✓ Trusted: git pull --rebase`

Trusted patterns persist for the session and are stored as regex in `allowedCommands`.

> If a command matches a `deniedCommands` pattern, granular options are not available — only allow once or trust the entire tool.

---

## Read and Write Path Trust Levels

When Kiro accesses files **outside the current working directory**, you get a path-specific picker:

```
Press (↑↓) to navigate (⏎) to select scope
> Specific paths    → ~/.config/app/settings.json
  Complete directory → ~/.config/app
  Entire Tool        → *
```

> Paths **within** the current working directory do NOT trigger the picker.