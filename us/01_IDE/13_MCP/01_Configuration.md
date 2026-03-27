# Model Context Protocol (MCP)

> **Source:** [kiro.dev/docs/mcp/](https://kiro.dev/docs/mcp/)

---

MCP is a protocol that allows Kiro to communicate with external servers to access specialized tools, prompts, and resources. For example, the AWS Documentation MCP server provides tools to search, read, and get recommendations from AWS documentation directly within Kiro.

With MCP, you can:
- Access specialized knowledge bases and documentation
- Integrate with external services and APIs
- Extend Kiro's capabilities with domain-specific tools
- Use server-provided prompt templates and resource templates via the `#` mention system in chat
- Respond to server elicitation requests when tools need additional input during execution
- Create custom tools for your specific workflows

---

## Setting Up MCP

### Prerequisites

Before using MCP:
1. Ensure you have the latest version of Kiro installed
2. Check each MCP server's documentation for specific prerequisites

### Enabling MCP Support

After creating your configuration file:
1. Open Settings with `Cmd+,` (Mac) or `Ctrl+,` (Windows/Linux)
2. Search for "MCP"
3. Enable the MCP support setting

### Using the MCP Servers Tab

The Kiro panel includes an **MCP servers tab** that shows:
- All configured MCP servers
- Connection status indicators
- Quick access to server tools

To use this feature:
1. Select the Kiro icon in the activity bar
2. Navigate to the **MCP servers** tab
3. Click any tool name to insert a placeholder prompt in the chat

---

## Configuration

MCP configuration files use JSON format:

```json
{
  "mcpServers": {
    "local-server-name": {
      "command": "command-to-run-server",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR1": "hard-coded-variable",
        "ENV_VAR2": "${EXPANDED_VARIABLE}"
      },
      "disabled": false,
      "autoApprove": ["tool_name1", "tool_name2"],
      "disabledTools": ["tool_name3"]
    },
    "remote-server-name": {
      "url": "https://endpoint.to.connect.to",
      "headers": {
        "HEADER1": "value1",
        "HEADER2": "value2"
      },
      "disabled": false,
      "autoApprove": ["tool_name1"],
      "disabledTools": ["tool_name3"]
    }
  }
}
```

### Configuration Locations

| Level | File | Scope |
|---|---|---|
| **Workspace** | `.kiro/settings/mcp.json` | Current workspace only — ideal for project-specific servers |
| **User** | `~/.kiro/settings/mcp.json` | All workspaces — best for frequently used servers |

> If both files exist, configurations are **merged** with workspace settings taking precedence.

### Creating Configuration Files

- **Command Palette:** `Cmd+Shift+P` → search "MCP" → "Kiro: Configure MCP Servers"
- **Kiro panel:** Navigate to MCP servers tab → click **+** to add a new server

### Environment Variables

```json
{
  "mcpServers": {
    "server-name": {
      "env": {
        "API_KEY": "${YOUR_API_KEY}",
        "DEBUG": "true",
        "TIMEOUT": "30000"
      }
    }
  }
}
```

### Disabling Servers Temporarily

```json
{
  "mcpServers": {
    "server-name": {
      "disabled": true
    }
  }
}
```

### Security Considerations

- Use environment variable references (`${API_TOKEN}`) instead of hardcoding sensitive values
- Never commit configuration files with credentials to version control
- Only connect to trusted remote servers
- Review tool permissions before adding them to `autoApprove`

---

## Troubleshooting

### Common Configuration Issues

1. **Validate JSON syntax** — Ensure no syntax errors, missing commas, quotes, or brackets
2. **Verify command paths** — Ensure the command exists in your PATH; try running it directly in your terminal
3. **Check environment variables** — Verify required env vars are set and correctly named
4. **Save configuration changes** — Changes apply automatically on save (`Cmd+S`)

### Checking MCP Logs

1. Open the Kiro panel
2. Select the **Output** tab
3. Choose **"Kiro - MCP Logs"** from the dropdown

---

## Next Steps

- [Configuring MCPs →](https://kiro.dev/docs/mcp/configuration/)
- [MCP Server management →](https://kiro.dev/docs/mcp/servers/)
- [Using MCP Tools →](https://kiro.dev/docs/mcp/usage/)
- [Best Practices / Security →](https://kiro.dev/docs/mcp/security/)
- [Official MCP Documentation →](https://modelcontextprotocol.io/introduction)
