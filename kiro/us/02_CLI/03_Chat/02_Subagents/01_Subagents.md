# Subagents

> **Source:** [kiro.dev/docs/cli/chat/subagents/](https://kiro.dev/docs/cli/chat/subagents/)

---

Subagents allow you to assign complex tasks to specialized agents with live progress tracking. Kiro can spawn subagents to work independently on subtasks while you monitor progress in real time.

---

## Key Capabilities

- **Autonomous execution** — Run independently with their own context
- **Live progress tracking** — Monitor real-time status updates as subagents work
- **Core tool access** — Read files, execute commands, write files, and use MCP tools
- **Parallel execution** — Run multiple subagents simultaneously for efficient task execution
- **Result aggregation** — Results automatically returned to the main agent when complete

---

## Default Subagent

Kiro includes a default subagent that handles general-purpose tasks. When you assign a task to a subagent without specifying a custom agent, the default subagent is used.

---

## Custom Subagents

You can spawn subagents using your own agent configurations:

```
> Use the backend agent to refactor the payment module
```

The subagent inherits the tool access and settings from that agent's configuration.

---

## How Subagents Work

1. **Task assignment** — You describe a task; Kiro determines if a subagent is appropriate
2. **Subagent initialization** — Created with its own context and tool access
3. **Autonomous execution** — Works through the task independently (may pause for tool permission approval)
4. **Progress updates** — You receive live progress updates showing current work
5. **Result return** — When complete, results are returned to the main agent

---

## Tool Availability

| Available | Not Available |
|---|---|
| `read` — Read files and directories | `web_search` — Web research |
| `write` — Create and edit files | `web_fetch` — Fetch URLs |
| `shell` — Execute bash commands | `introspect` — CLI info |
| `code` — Code intelligence | `thinking` — Reasoning tool |
| MCP tools | `todo_list` — Task tracking |
| | `use_aws` — AWS commands |
| | `grep` — Search file contents |
| | `glob` — Find files by pattern |

If your custom agent config includes unavailable tools, they are simply skipped — the agent still functions with available tools.

---

## Configuring Subagent Access

### Restricting Available Agents

In your agent config, specify which agents can be used as subagents using `allowedAgents`.

### Trusting Specific Agents

Use `trustedAgents` to allow specific subagents to run without permission prompts.

### Combining Both Settings

You can combine `allowedAgents` and `trustedAgents` for fine-grained control over which agents run automatically and which require approval.