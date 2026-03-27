# Completions & Autocomplete

> **Source:** [kiro.dev/docs/cli/autocomplete/](https://kiro.dev/docs/cli/autocomplete/)

---

Kiro CLI provides AI-powered command completions and suggestions for hundreds of popular CLI tools, making command-line work faster and more accurate.

---

## Autocomplete Dropdown Menu

The autocomplete dropdown appears to the **right of your cursor** when typing commands, showing available options, subcommands, and arguments that you can select using arrow keys.

### Using Autocomplete

- Start typing a command
- The dropdown appears automatically with suggestions
- Use **arrow keys** to navigate
- Press **Tab** or **Enter** to accept a suggestion

### Configuration

Autocomplete behavior can be configured in your Kiro CLI settings. See the [CLI settings reference](https://kiro.dev/docs/cli/reference/) for available options.

---

## Inline Suggestions

Inline suggestions appear as gray **"ghost text"** directly on your command line as you type. This feature works independently from the dropdown menu.

### Using Inline Suggestions

- Type the beginning of a command
- Ghost text appears showing the predicted completion
- Press **Tab** to accept the full suggestion
- Press **→** (right arrow) to accept word by word
- Continue typing to dismiss and override the suggestion

### Managing Inline Suggestions

Toggle inline suggestions on/off in your shell configuration or CLI settings.

---

## Supported Tools

Kiro CLI provides completions for hundreds of popular tools including:

**Popular tools:** `git`, `docker`, `kubectl`, `npm`, `yarn`, `pip`, `cargo`, `make`, `terraform`, `aws`

**Language tools:** `node`, `python`, `go`, `ruby`, `java`, `rustc`, `gcc`, `mvn`, `gradle`

**System tools:** `ls`, `cd`, `grep`, `find`, `curl`, `ssh`, `chmod`, `systemctl`

---

## Troubleshooting

### Autocomplete Not Working

- Verify Kiro CLI is properly installed and in your PATH
- Restart your terminal after installation
- Check that the shell integration is enabled in your profile (`.bashrc`, `.zshrc`, etc.)

### Inline Suggestions Issues

- Ensure your terminal emulator supports the required escape sequences
- Check that inline suggestions are enabled in your Kiro CLI configuration
