# Custom Agents — Kiro CLI

> **Source:** [kiro.dev/docs/cli/custom-agents/](https://kiro.dev/docs/cli/custom-agents/)

---

Custom agents allow you to create and deploy specialized AI agents tailored to specific workflows, with fine-grained control over tools, context, and behavior.

---

## Benefits of Using Custom Agents

1. **Workflow optimization** — Create agents tailored to specific tasks like AWS infrastructure management, code reviews, or debugging sessions.
2. **Reduced interruptions** — Pre-approve trusted tools to eliminate permission prompts during focused work sessions.
3. **Enhanced context** — Automatically include relevant project documentation, configuration files, or system information.
4. **Team collaboration** — Share custom agent configurations with team members to ensure consistent development environments.
5. **Security control** — Limit tool access to only what's needed for specific workflows, reducing potential security risks.

---

## Relationship to MCP and Built-in Tools

Custom agents work with both built-in tools and external tools provided through the Model Context Protocol (MCP):

- **Use built-in tools** — File operations, command execution, AWS CLI integration, and other core functionality
- **Integrate MCP servers** — Add custom tools and services through MCP server configurations
- **Control tool access** — Specify exactly which tools from each source are available
- **Manage tool conflicts** — Use aliases to handle naming conflicts between different tool sources

---

## Next Steps

- [Creating custom agents →](https://kiro.dev/docs/cli/custom-agents/creating/)
- [Agent configuration reference →](https://kiro.dev/docs/cli/custom-agents/configuration-reference/)
- [Sharing agents →](https://kiro.dev/docs/cli/custom-agents/sharing/)
