# Model Context Protocol (MCP) — CLI

> **Source:** [kiro.dev/docs/cli/mcp/](https://kiro.dev/docs/cli/mcp/)

---

MCP is a protocol that allows Kiro to communicate with external servers to access specialized tools and information.

With MCP, you can:
- Access specialized knowledge bases and documentation
- Integrate with external services and APIs
- Extend Kiro's capabilities with domain-specific tools
- Create custom tools for your specific workflows

---

## Setting Up MCP

There are two ways to configure MCP servers in Kiro CLI:

### 1. Command Line

```bash
kiro-cli mcp add \
  --name "awslabs.aws-documentation-mcp-server" \
  --scope global \
  --command "uvx" \
  --args "awslabs.aws-documentation-mcp-server@latest" \
  --env "FASTMCP_LOG_LEVEL=ERROR" \
  --env "AWS_DOCUMENTATION_PARTITION=aws"
```

### 2. mcp.json File

MCP servers can be loaded from:
- Workspace level: `<project-root>/.kiro/settings/mcp.json`
- User level: `~/.kiro/settings/mcp.json`

```json
{
  "mcpServers": {
    "local-server-name": {
      "command": "command-to-run-server",
      "args": ["arg1", "arg2"],
      "env": {
        "ENV_VAR1": "value1",
        "ENV_VAR2": "value2"
      },
      "disabled": false
    },
    "http-server-with-oauth": {
      "type": "http",
      "url": "https://api.example.com/mcp",
      "oauth": {
        "redirectUri": "127.0.0.1:8080",
        "oauthScopes": ["read", "write"]
      }
    }
  }
}
```

For HTTP-based MCP servers requiring OAuth:
- `oauth.redirectUri` — Custom redirect URI for OAuth flow (optional)
- `oauth.oauthScopes` — Array of OAuth scopes to request (optional)

> If you encounter OAuth scope errors, use an empty array: `"oauthScopes": []`

### 3. Agent Configuration

The `mcpServers` field specifies which MCP servers a custom agent has access to:

```json
{
  "name": "myagent",
  "description": "My special agent",
  "mcpServers": {
    "fetch": {
      "command": "fetch3.1",
      "args": []
    }
  },
  "includeMcpJson": false
}
```

> `includeMcpJson: true` gives the agent access to all MCP servers defined in user and workspace level configurations in addition to those in the agent's `mcpServers` field.

---

## Troubleshooting

### Tool Validation Errors

Verify the MCP server is running and accessible. Check the server's documentation for required configuration.

### Large Description Warnings

Some MCP servers provide very large tool descriptions. This can impact performance. Consider using a more specific server or filtering tools if available.

---

## Additional Resources

- [MCP Server Registry →](https://kiro.dev/docs/cli/mcp/registry/)
- [MCP Examples →](https://kiro.dev/docs/cli/mcp/examples/)
- [MCP Security →](https://kiro.dev/docs/cli/mcp/security/)