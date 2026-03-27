# Codebase Indexing

> **Source:** [kiro.dev/docs/editor/codebase-indexing/](https://kiro.dev/docs/editor/codebase-indexing/)

---

Kiro indexes your codebase to provide intelligent, context-aware code assistance. Understanding how indexing works helps you get the most out of Kiro's AI features.

---

## When Indexing Occurs

### Automatic Indexing

Kiro performs indexing automatically in these scenarios:

1. **Project Import** — When you first open a project in Kiro, it automatically begins indexing all files in your workspace.
2. **File Changes** — When new files are created or added to your project, they are automatically indexed.
3. **External Changes** — When files are modified outside of Kiro (e.g., through git operations), they are re-indexed.

### Manual Indexing

You can trigger indexing manually when needed using the **Command Palette**:
- macOS: `Cmd+Shift+P`
- Windows/Linux: `Ctrl+Shift+P`

---

## Available Indexing Commands

![Kiro Indexing](https://kiro.dev/images/kiro-indexing.png)

### Codebase Indexing

| Command | When to Use |
|---|---|
| `Kiro: Codebase Force Re-Index` | Forces a complete re-indexing of your entire codebase. Use when: index seems corrupted or incomplete, major structural changes were made, or suggestions seem outdated. |
| `Kiro: Rebuild codebase index` | Completely rebuilds the codebase index from scratch. More thorough than force re-indexing. Use when the index appears severely corrupted or you experience persistent issues. |

### Documentation Indexing

| Command | Description |
|---|---|
| `Kiro: Docs Index` | Initiates indexing of documentation files in your project |
| `Kiro: Docs Force Re-Index` | Forces a complete re-indexing of all documentation files |

---

## Monitoring Indexing Progress

![Kiro Indexing Logs](https://kiro.dev/images/kiro-indexing-logs.png)

You can monitor the indexing process through the **Kiro Logs** panel:

1. Access the **Output** panel in Kiro
2. Select **"Kiro Logs"** from the dropdown menu
3. View real-time indexing progress and status updates

The logs show:
- When indexing starts and completes
- Number of files found and processed
- Progress percentage for large codebases
- Completion time for indexing operations

---

## Indexed Content

Kiro indexes various types of content to provide intelligent assistance:

| Content Type | Examples |
|---|---|
| **Source Code** | All programming language files in your workspace |
| **Documentation** | Markdown, MDX, and other documentation formats |
| **Configuration** | Project configuration files and manifests |
| **Dependencies** | Package definitions and dependency information |

The indexed data enables features like:
- Intelligent code completion
- Cross-file navigation
- Context-aware suggestions
- Documentation lookup
- Code refactoring assistance