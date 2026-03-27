# Hooks — Kiro CLI

> **Source:** [kiro.dev/docs/cli/hooks/](https://kiro.dev/docs/cli/hooks/)

---

Hooks allow you to execute custom commands at specific points during agent lifecycle and tool execution. They enable you to automatically validate actions, inject context, or run post-processing tasks.

---

## Defining Hooks

Hooks are defined in the agent configuration file. See the [Agent Configuration Reference](https://kiro.dev/docs/cli/custom-agents/configuration-reference#hooks-field) for the complete syntax.

---

## Hook Event

Hooks receive a hook event in **JSON format via STDIN**:

```json
{ "hook_event_name": "agentSpawn", "cwd": "/current/working/directory" }
```

For tool-related hooks, additional fields are included:
- `tool_name` — Name of the tool being executed
- `tool_input` — Tool-specific parameters
- `tool_response` — Tool execution results *(PostToolUse only)*

---

## Hook Output

| Exit Code | Behavior |
|---|---|
| `0` | Hook succeeded. STDOUT is captured but not shown to user. |
| `2` | *(PreToolUse only)* Block tool execution. STDERR is returned to the LLM. |
| Other | Hook failed. STDERR is shown as a warning to user. |

---

## Tool Matching

Use the `matcher` field to specify which tools the hook applies to:

| Matcher | Matches |
|---|---|
| `"fs_write"` or `"write"` | Write tool |
| `"fs_read"` or `"read"` | Read tool |
| `"execute_bash"` or `"shell"` | Shell command execution |
| `"use_aws"` or `"aws"` | AWS CLI tool |
| `"@git"` | All tools from git MCP server |
| `"@git/status"` | Specific tool from git MCP server |
| `"*"` | All tools (built-in and MCP) |
| `"@builtin"` | All built-in tools only |
| *(no matcher)* | Applies to all tools |

---

## Hook Types

### AgentSpawn

Runs when agent is activated. No tool context provided.

```json
{ "hook_event_name": "agentSpawn", "cwd": "/current/working/directory" }
```
- Exit `0`: STDOUT is added to agent's context
- Other: Show STDERR warning to user

---

### UserPromptSubmit

Runs when user submits a prompt. Output is added to conversation context.

```json
{ "hook_event_name": "userPromptSubmit", "cwd": "/current/working/directory", "prompt": "user's input prompt" }
```
- Exit `0`: STDOUT is added to agent's context
- Other: Show STDERR warning to user

---

### PreToolUse

Runs **before** tool execution. Can validate and block tool usage.

```json
{
  "hook_event_name": "preToolUse",
  "cwd": "/current/working/directory",
  "tool_name": "read",
  "tool_input": { "operations": [{ "mode": "Line", "path": "/docs/hooks.md" }] }
}
```
- Exit `0`: Allow tool execution
- Exit `2`: Block tool execution, return STDERR to LLM
- Other: Show STDERR warning, allow tool execution

---

### PostToolUse

Runs **after** tool execution with access to tool results.

```json
{
  "hook_event_name": "postToolUse",
  "tool_name": "read",
  "tool_input": { ... },
  "tool_response": { "success": true, "result": ["..."] }
}
```
- Exit `0`: Hook succeeded
- Other: Show STDERR warning (tool already ran)

---

### Stop

Runs when the assistant finishes responding (end of each turn). Useful for post-processing: compilation, testing, formatting, or cleanup.

```json
{ "hook_event_name": "stop", "cwd": "/current/working/directory" }
```

> Note: Stop hooks do not use matchers since they don't relate to specific tools.

---

### MCP Tool Example

For MCP tools, the tool name includes the full namespaced format:

```json
{
  "hook_event_name": "preToolUse",
  "tool_name": "@postgres/query",
  "tool_input": { "sql": "SELECT * FROM orders LIMIT 10;" }
}
```

---

## Timeout

Default timeout is **30 seconds** (30,000ms). Configure with the `timeout_ms` field in your agent configuration.

---

## Caching

Successful hook results are cached based on `cache_ttl_seconds`:

| Value | Behavior |
|---|---|
| `0` | No caching (default) |
| `> 0` | Cache successful results for specified seconds |
| — | `AgentSpawn` hooks are never cached |
