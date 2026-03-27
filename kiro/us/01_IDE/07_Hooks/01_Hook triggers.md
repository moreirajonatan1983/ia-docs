# Hooks

> **Source:** [kiro.dev/docs/hooks/](https://kiro.dev/docs/hooks/)

---

Agent hooks are automated triggers that execute predefined agent prompts or shell commands when specific events occur in your IDE. Rather than manually asking for routine tasks, hooks set up automated responses to events.

---

## What are Agent Hooks?

![Kiro Hook](https://kiro.dev/videos/kiro-hook.mp4)


Hooks can trigger on:
- Saving, creating, or deleting files
- User prompt submission and agent turn completion
- Before or after tool invocations
- Before or after spec task execution
- Manual triggers on demand

**Benefits of agent hooks:**
- Maintain consistent code quality automatically
- Prevent security vulnerabilities
- Reduce manual overhead
- Standardize team processes
- Create faster development cycles

---

## How Agent Hooks Work

The agent hook system follows a simple two-step process:

1. **Event Detection** — The system monitors for specific events in your IDE
2. **Automated Action** — When an event occurs, an action (agent prompt or shell command) is executed

---

## Setting Up Agent Hooks

### Creating a Hook

1. Navigate to the **Agent Hooks** section in the Kiro panel
2. Click the **+** button to create a new hook
3. Choose how you want to create the hook:
   - **Manually create a hook** — configure a hook by hand in a form
   - **Ask Kiro to create a hook** — describe a hook using natural language

You can also open the Hook UI from the Command Palette:
- macOS: `Cmd + Shift + P` → `Kiro: Open Kiro Hook UI`
- Windows/Linux: `Ctrl + Shift + P` → `Kiro: Open Kiro Hook UI`

---

### Ask Kiro to Create a Hook

1. Select **Ask Kiro to create a hook**
2. Describe the hook workflow in natural language
3. Press Enter or click **Submit**
4. Review the generated configuration, adjust if needed, and click **Save Hook**

---

### Manually Create a Hook

1. Select **Manually create a hook** to open the hook form
2. Fill in the form fields:

| Field | Description |
|---|---|
| **Title** | A short name for the hook |
| **Description** | What the hook does |
| **Event** | The trigger type (e.g., File Save, Post Tool Use, Pre Task Execution) |
| **Tool name** | For Pre/Post Tool Use hooks, specify which tools to match |
| **File pattern** | For file event hooks, specify which files to match (e.g., `src/**/*.tsx`) |
| **Action** | Choose **Ask Kiro** (agent prompt) or **Run Command** (shell command) |
| **Instructions or Command** | The prompt or shell command to execute |

3. Click **Create Hook** when done, or **Clear** to reset the form

---

## Next Steps

- [Hook triggers →](https://kiro.dev/docs/hooks/hook-triggers/)
- [Hook actions →](https://kiro.dev/docs/hooks/hook-actions/)
- [Examples →](https://kiro.dev/docs/hooks/examples/)
- [Management →](https://kiro.dev/docs/hooks/management/)
- [Best practices →](https://kiro.dev/docs/hooks/best-practices/)
- [Troubleshooting →](https://kiro.dev/docs/hooks/troubleshooting/)