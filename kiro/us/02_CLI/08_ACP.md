# Agent Client Protocol (ACP)

> **Source:** [kiro.dev/docs/cli/acp/](https://kiro.dev/docs/cli/acp/)

---

ACP (Agent Client Protocol) is a standardized protocol for agent-editor communication — similar to how the Language Server Protocol (LSP) standardized language server integration. Agents that implement ACP work with any compatible editor, and editors that support ACP gain access to all ACP-compatible agents.

---

## What is ACP?

AI coding agents and editors are tightly coupled without a standard. Each editor must build custom integrations for every agent, creating integration overhead, limited compatibility, and developer lock-in.

ACP solves this by providing a standardized protocol. Kiro CLI implements ACP so it can be used as an AI agent in any ACP-compatible editor (JetBrains, Zed, etc.).

---

## Quick Start

Run Kiro as an ACP agent:
```bash
kiro-cli acp
```

Use a specific agent configuration:
```bash
kiro-cli acp --agent my-agent
```

The agent communicates over **stdin/stdout** using **JSON-RPC 2.0**. Configure your editor to spawn this command.

---

## Editor Setup

### General

Use the **full path** to `kiro-cli` in your editor configuration. IDEs often don't inherit your shell's PATH, so commands like `kiro-cli` may not be found.

Find the path:
```bash
which kiro-cli
# Commonly: ~/.local/bin/kiro-cli on Linux/macOS
```

### JetBrains IDEs

Configure via the **JetBrains AI plugin** settings. Add Kiro CLI as an ACP-compatible agent using the full path.

### Zed

Configure in `~/.config/zed/settings.json` under the `assistant` section. Set the command to the full path of `kiro-cli acp`.

### Other Editors

Any editor supporting the ACP protocol can use Kiro CLI. Refer to the specific editor's documentation for configuring ACP agents.

---

## Supported ACP Methods

Kiro CLI implements the ACP specification including:
- **Core protocol** — Session management, model selection, and streaming responses
- **Agent capabilities** — Tool access, context management, and conversation state
- **Session updates** — Real-time streaming of agent responses

---

## Kiro Extensions

Kiro extends ACP with custom methods (prefixed with `_kiro.dev/` per the ACP spec) to expose Kiro-specific features:

- [Slash commands](https://kiro.dev/docs/cli/reference/slash-commands)
- [MCP server events](https://kiro.dev/docs/cli/mcp)
- [Context compaction](https://kiro.dev/docs/cli/chat#context-management)

Clients that don't support these extensions can safely ignore them — they're optional enhancements.

> Note: These extensions are **experimental** and subject to change in future releases.

---

## Session Storage

Sessions are stored locally and can be resumed. The session ID is included in ACP responses to allow clients to reference specific sessions.

## Logging

Use the `--log-level` flag to control logging verbosity when running in ACP mode. Logs are written to stderr to avoid interfering with the JSON-RPC communication on stdout.