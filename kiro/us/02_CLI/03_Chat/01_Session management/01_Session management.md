# Chat — Kiro CLI

> **Source:** [kiro.dev/docs/cli/chat/](https://kiro.dev/docs/cli/chat/)

---

## Starting a Session

```bash
kiro-cli
```

Or start a chat with a specific agent:
```bash
kiro-cli --agent myagent
```

---

## Entering Multi-line Statements

To enter multi-line statements, use the `/editor` command or press `Ctrl(^) + J` to insert a new line.

The `/editor` command opens your default editor (defaults to `vi`) where you can compose longer, multi-line prompts. After you save and close the editor, the content is sent as your message to Kiro.

You can also use the `/reply` command to open your editor with the most recent assistant message quoted for reply — useful for multi-line responses to previous messages.

---

## Conversation Persistence

Kiro remembers your conversations based on the folder where you started them. When you start a session in a directory where you previously chatted with Kiro, you can tell Kiro to automatically load that conversation history.

### Directory-based Persistence

Resume a conversation in the current directory:
```bash
kiro-cli chat --resume
```

Open an interactive session picker to choose from previous sessions:
```bash
kiro-cli chat --resume-picker
```

### Starting a Fresh Conversation

Use the `/chat new` command without restarting the CLI. This saves your current session to the database and begins a new one:

```bash
# Start a fresh conversation
/chat new

# Start a fresh conversation with an initial prompt
/chat new how do I set up a React project
```

Use `/chat resume` to return to any previous session.

### Manually Saving and Loading Conversations

While in a chat session:

```bash
# Save current conversation to a JSON file
/chat save ./my-project-conversation
/chat save ./my-project-conversation -f   # overwrite existing
/chat save /home/user/project/my-project-conversation.json

# Load a conversation from a previously saved JSON file
/chat load ./my-project-conversation.json
```

> Note: You cannot use `~` to denote your home directory in the path. The `/chat save` and `/chat load` commands operate independently of the directory where the conversation was originally created.