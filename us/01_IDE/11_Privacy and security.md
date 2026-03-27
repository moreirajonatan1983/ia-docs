# Privacy and Security

> **Source:** [kiro.dev/docs/privacy-and-security/](https://kiro.dev/docs/privacy-and-security/)

---

Kiro provides various security features to help you maintain control over your development environment. Understanding these features helps you implement appropriate safeguards for your specific needs.

---

## URL Fetching

In the Kiro chat module, you can paste a specific URL for your device to fetch and use it as context. You are responsible for the URL content that you fetch and ensuring that your use complies with any applicable third-party terms and laws.

---

## Autopilot vs. Supervised Mode

Kiro operates in two modes. **Autopilot is enabled by default.**

### Autopilot Mode

In Autopilot mode, Kiro works **autonomously**:
- Executes multiple steps without requiring approval for each one
- Makes decisions based on its understanding of your requirements
- Includes file creation, modification, searching, and deletion
- Can run commands that impact the filesystem
- You can toggle autopilot on/off in the chat interface at any time
- You can **interrupt autopilot at any time** to regain manual control

### Supervised Mode

In supervised mode, Kiro works **interactively** with the user:
- Suggests actions (file creation, modification, deletion) but **waits for user confirmation** before proceeding
- Asks clarifying questions when needed
- You can review and approve each generated document or code change
- Maintains full control over the development process

### Viewing and Reverting Changes

In either mode, you can:
- View individual or all file changes by selecting **"View all changes"** in the Chat module
- Select **"Revert all changes"** to undo all agent modifications
- Revert to a [checkpoint](https://kiro.dev/docs/chat/checkpoints) to restore files to a previous state locally

---

## Trusted Commands

By default, Kiro requires **approval before running any command**. You can configure a trusted commands list in settings:

**Settings → Search for:** `Kiro Agent: Trusted Commands`

Kiro uses simple string prefix matching:

| Pattern | Behavior |
|---|---|
| `npm install` | Exact match — trusts only this exact command |
| `npm *` | Wildcard — trusts all npm commands |
| `*` | Universal — trusts **all** commands *(use with extreme caution)* |

> ⚠️ The system treats entire commands as single strings and only checks if they start with trusted patterns. It does **not** analyze command structure, chains, or special characters. Configure trusted patterns carefully.

---

## Best Practices

The following are general guidelines — they don't represent a complete security solution. Evaluate what's appropriate for your environment.

### Protecting Your Resources

When using GitHub or Google authentication with Kiro, be aware that the Kiro agent operates within your local environment and may access:
- Local files and repositories
- Environment variables
- AWS credentials stored in your environment
- Other configuration files with sensitive information

### Recommendations

**1. Workspace Isolation**
- Keep sensitive projects in separate workspaces
- Use `.gitignore` (or `.kiroignore`) to prevent access to sensitive files
- Consider using workspace trust features in your IDE

**2. Use a Clean Environment**
- Consider creating a dedicated user account or container environment for Kiro
- Limit access to only the repositories and resources needed for your current project

**3. Manage AWS Credentials Carefully**
- Use temporary credentials with appropriate permissions
- Consider using AWS named profiles to isolate Kiro's access
- For sensitive work, remove AWS credentials from your environment when not needed

**4. Repository Access Control**
- When using GitHub authentication, review which repositories Kiro can access
- Use repository-specific access tokens when possible
- Regularly audit access permissions

---

## Remote Extensions Security

Remote extension support follows the same security model as local extensions. When using remote development (SSH, containers, WSL), extensions run in the remote environment with the permissions of the remote user. Ensure remote environments are properly secured and only trusted extensions are installed.
