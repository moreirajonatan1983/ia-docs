# Autopilot

> **Source:** [kiro.dev/docs/chat/autopilot/](https://kiro.dev/docs/chat/autopilot/)

---

Autopilot mode is Kiro's autonomous execution mode that allows the agent to make code changes across your codebase and complete complex tasks with minimal intervention.

---

## What is Autopilot Mode?

Autopilot mode enables Kiro to work more independently on your behalf — creating files, modifying code across multiple locations, running commands, and making architectural decisions without asking for approval at each step.

---

## How It Works

### Autopilot Mode *(default)*

Kiro works **autonomously** to complete tasks end-to-end:
- Can create files, modify code across multiple locations, and run commands
- Makes architectural decisions without asking for approval at each step
- You maintain control through the ability to view all changes, revert everything, or interrupt at any time

### Supervised Mode

Kiro works **turn-by-turn** with your approval:
- Yields for your approval after each turn that contains file edits
- Changes are presented as **individual hunks** (logical groups of related lines)
- Each hunk can be independently accepted, rejected, or discussed with inline chat
- You can accept changes at the file level or accept all changes at once
- Full visibility into each change; fine-grained control over the development process

---

## Switching Between Modes

You can **toggle between modes at any time** in the chat interface based on your current needs and comfort level with the task at hand.

---

## When to Use Each Mode

| Mode | Best For |
|---|---|
| **Autopilot** | Experienced users familiar with Kiro, repetitive or well-defined tasks, projects where you want to move quickly, tasks spanning multiple files or requiring several steps |
| **Supervised** | New users getting familiar with Kiro, critical or sensitive codebases, learning how Kiro approaches problems, when you want to carefully review each change, working with unfamiliar or complex systems |

---

## Change Management Features

### In Autopilot Mode

You maintain control through several key features:

| Feature | Description |
|---|---|
| **View All Changes** | Select "View all changes" in the Chat module to see a comprehensive diff of all modifications |
| **Revert All Changes** | Select "Revert" to restore all files to their previous state locally (essentially an undo for all Kiro modifications) |
| **Checkpoint Revert** | Revert to a [checkpoint](https://kiro.dev/docs/chat/checkpoints) — reverts both file changes and context additions |
| **Interrupt Execution** | Stop Kiro mid-execution at any time to regain manual control |

### In Supervised Mode

| Feature | Description |
|---|---|
| **Review changes** | Kiro shows exactly what was modified, with line change indicators (+x -y lines) visible in chat |
| **Per-file review** | When multiple files are edited, review and accept/reject changes per file |
| **Hunk-based review** | For file modifications, Kiro presents changes as individual hunks that can be independently accepted, rejected, or discussed |
| **Per-hunk actions** | Accept, Reject, or Chat inline about any specific hunk |
| **Selective approval** | Accept some hunks while rejecting others within the same file |
| **Accept All / Reject All** | Accept All applies all pending changes and continues; Reject All reverts everything |
