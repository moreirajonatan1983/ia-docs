# Chat

> **Source:** [kiro.dev/docs/chat/](https://kiro.dev/docs/chat/)

---

Kiro's chat interface is the primary way to interact with the AI agent for contextual conversations, development assistance, and code generation.

---

## Getting Started

### Accessing Chat

| Method | Shortcut |
|---|---|
| Keyboard shortcut | `Cmd+L` (Mac) / `Ctrl+L` (Windows/Linux) |
| Command Palette | `Cmd+Shift+P` → search "Kiro: Open Chat" |
| Secondary Side Bar | `Cmd+Opt+B` (Mac) / `Ctrl+Alt+B` (Windows/Linux) |

### Multi-language Support

Kiro chat supports multiple natural languages including: Mandarin, French, German, Italian, Japanese, Spanish, Korean, Hindi, Portuguese, and more. Kiro automatically detects your language and responds in the same language.

### Your First Conversation

1. Type your question or request in natural language in the chat input
2. Press **Enter** to send
3. Kiro will analyze your request and respond appropriately

**Example requests:**
```
"Explain how authentication works in this project"
"Create a React component for a user profile page"
"Help me fix the error in this function"
```

### Exporting a Conversation

Right-click the tab of the conversation → **Export Conversation** → saves as `.md` format.

### Smart Intent Detection

Kiro intelligently detects your intent:
- **Information requests** ("How does this work?", "What's the purpose of this code?") → Responds with explanations without modifying code
- **Action requests** ("Create a component", "Fix this bug") → Proposes or implements code changes

---

## Context Management

### Context Providers

Use the `#` symbol in the chat input to access context providers:

| Provider | Example Usage |
|---|---|
| `#codebase` | `#codebase explain the authentication flow` |
| `#file` | `#auth.ts explain this implementation` |
| `#folder` | `#components/ what components do we have?` |
| `#git diff` | `#git diff explain what changed in this PR` |
| `#terminal` | `#terminal help me fix this build error` |
| `#problems` | `#problems help me resolve these issues` |
| `#url` | `#url:https://docs.example.com/api explain this API` |
| `#code` | `#code:const sum = (a, b) => a + b; explain this function` |
| `#repository` | `#repository how is this project organized?` |
| `#current` | `#current explain this component` |
| `#steering` | `#steering:coding-standards.md review my code` |
| `#docs` | `#docs:api-reference.md explain this API endpoint` |
| `#spec` | `#spec:user-authentication update the design file` |
| `#mcp` | `#mcp:aws-docs how do I configure S3 buckets?` |

Combine multiple context providers:
```
#codebase #auth.ts explain how authentication works with our database
```

The `#terminal` context provider is particularly powerful for debugging:
```
#terminal My build is failing, what's the issue?
#terminal These tests aren't passing, help me understand why
#terminal npm install is throwing errors
```

---

## Sessions and History

### Managing Sessions

- **New Session:** Click the **+** icon in the chat panel
- **Switch Sessions:** Navigate using the tab switcher
- **View History:** Click the **History** button
- **Task Tracking:** Monitor progress via the **Task list** button

### Execution History

Kiro maintains a detailed history of sessions including: code changes, commands executed, search results, and file operations. You can **search**, **restore**, or **delete** specific sessions.