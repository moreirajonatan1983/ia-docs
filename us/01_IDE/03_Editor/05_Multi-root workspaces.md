# Multi-root Workspaces

> **Source:** [kiro.dev/docs/editor/multi-root-workspaces/](https://kiro.dev/docs/editor/multi-root-workspaces/)

---

Multi-root workspaces allow you to work with multiple project folders simultaneously in a single Kiro window. Kiro's AI features are designed to work seamlessly across all root folders.

---

## Core Functionality

Kiro will resolve file paths intelligently across all root folders as it navigates and updates your multi-root workspace.

**[Codebase Indexing](https://kiro.dev/docs/editor/codebase-indexing/)** and Repository Maps work seamlessly in multi-root workspaces — both indices contain code from all root folders and can be referenced in prompts exactly as in single-root workspace scenarios.

When adding a file using the `#file` context provider, if there are multiple files with the same name in different root folders, Kiro will display a list of matching files with their paths so you can select the correct one.

---

## Specs

Kiro retrieves all [spec](https://kiro.dev/docs/specs/) files from the `.kiro` subfolder under **each** of the root folders, and displays them as a unified list in the Specs section of the Kiro panel. The name of the containing root folder is displayed next to each spec.

- You can ask Kiro to work on a spec defined under any of the root folders.
- When creating a new spec, Kiro will determine the appropriate root folder to place it into.

---

## Steering Files

Kiro retrieves all [steering](https://kiro.dev/docs/steering/) files from the `.kiro` subfolder under each root folder, displaying them as a unified list in the **Agent Steering** section of the Kiro panel under the *Workspace* group. The root folder name is displayed next to each workspace steering file.

| Directive | Behavior |
|---|---|
| **Always Included** | Steering files are always loaded, regardless of which root folder the agent is working on |
| **Conditional Inclusion** | Loaded only if the agent is working on a file in that same root, and the file matches the inclusion pattern |

When creating a new workspace steering file, you will be prompted to pick the root folder to save it into.

---

## Hooks

Kiro retrieves all [hooks](https://kiro.dev/docs/hooks/) from the `.kiro` subfolder under each root folder, displaying them as a unified list in the **Agent Hooks** section. The root folder name is displayed next to each hook.

> **Important:** File Create, File Save, and File Delete hooks are triggered **only** when the agent modifies files located in the same root folder where the hook is defined.

When creating a new hook, you will be prompted to pick the root folder.

---

## MCP Servers

Kiro retrieves all [MCP server](https://kiro.dev/docs/mcp/) definitions from the `.kiro` subfolder under each root folder, displaying them as a unified list in the **MCP Servers** section.

- All MCP servers defined in all roots are initialized at startup.
- If two root folders define an MCP server with the same name, the definition in the **last defining root** is used.
- Servers are launched with the **first root folder** as their current working directory.

> When you click **Open MCP config**, you see the user-level (global) MCP configuration by default. Click **Workspace Config** to view workspace-level configuration. In a multi-root workspace, you'll be prompted to pick the root folder.