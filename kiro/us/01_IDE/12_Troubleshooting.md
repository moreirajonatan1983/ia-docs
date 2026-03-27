# Troubleshooting

> **Source:** [kiro.dev/docs/troubleshooting/](https://kiro.dev/docs/troubleshooting/)

---

## Kiro Installation Issues

### macOS: "Kiro is damaged and can't be opened"

This pop-up is a **false positive** in macOS security features (Gatekeeper).

**Solutions (try in order):**

1. Go to **System Settings → Privacy & Security** and click **Allow** or **Open anyway** for Kiro.
2. Drag `Kiro.app` to your desktop, then drag it back to the Applications folder.
3. Restart your computer.
4. Open Terminal and run:
   ```bash
   sudo xattr -d com.apple.quarantine /Applications/Kiro.app
   ```

---

## Authentication Issues

### Browser Redirect Failures During Authentication

If Kiro doesn't redirect you to a browser during authentication:

**macOS:**
1. Open Kiro → **Help → Toggle Developer Tools**
2. Navigate to the **Console** tab
3. Observe any errors during the sign-in process
4. Verify `ioreg` is in your PATH:
   ```bash
   echo $PATH
   which ioreg
   # If missing, typically located at /usr/sbin/ioreg
   ```

**Windows:**
1. Open Command Prompt as administrator
2. Run Kiro with logging:
   ```
   C:\path\to\app.exe --enable-logging
   ```
3. Check logs for access denied errors — ensure your user has administrator permissions

### AWS IAM Identity Center Issues

**Q Developer Pro subscription required:**
If you see *"There was an error signing you in"*, ensure you have a valid **Q Developer Pro** subscription. [View subscription status →](https://docs.aws.amazon.com/amazonq/latest/qdeveloper-ug/q-admin-setup-subscribe-general.html)

**Regional limitations:**
Kiro defaults to **US East (N. Virginia)** for Identity Center authentication. If your Q Developer profile is in a different region, sign in using Builder ID, Google, or GitHub instead.

**Session duration and timeouts:**
Identity Center sessions have a default timeout of **8 hours**. Administrators can configure longer session timeouts in [AWS documentation →](https://docs.aws.amazon.com/singlesignon/latest/userguide/user-session-duration-how-to-configure.html)

---

## Shell Integration Issues

### Quick Fix: "Shell Integration Unavailable"

1. **Update Kiro:** `Cmd+Shift+P` / `Ctrl+Shift+P` → `Kiro: Check for Updates`
2. **Enable Integration:** `Cmd+Shift+P` / `Ctrl+Shift+P` → `Kiro: Enable Shell Integration`
3. **Restart** Kiro

### Manual Installation

If automatic setup fails, add to your shell config:

**Zsh (`~/.zshrc`):**
```bash
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path zsh)"
```

**Bash (`~/.bashrc`):**
```bash
[[ "$TERM_PROGRAM" == "kiro" ]] && . "$(kiro --locate-shell-integration-path bash)"
```

**Fish (`~/.config/fish/config.fish`):**
```fish
string match -q "$TERM_PROGRAM" "kiro" and . (kiro --locate-shell-integration-path fish)
```

**PowerShell (`$Profile`):**
```powershell
if ($env:TERM_PROGRAM -eq "kiro") { . "$(kiro --locate-shell-integration-path pwsh)" }
```

### Kiro Stuck in "Working..." Status / Terminal Output Not Visible

Caused by shell customizations that interfere with terminal integration (e.g., `bash-it`, `Oh My Posh`, `Powerlevel10k`).

**Powerlevel10k users** — Add to `~/.p10k.zsh`:
```bash
typeset -g POWERLEVEL9K_TERM_SHELL_INTEGRATION=true
```

Or disable customizations only when running inside Kiro (`~/.zshrc`):
```bash
if [[ "$TERM_PROGRAM" == "kiro" ]]; then
  # Leave empty
else
  ZSH_THEME="powerlevel10k/powerlevel10k"
fi
```

**Fish shell users** — Update the shell integration script to include `"kiro"`:

File: `/Applications/Kiro.app/Contents/Resources/app/out/vs/workbench/contrib/terminal/common/scripts/shellIntegration.fish`

Change:
```
string match --quiet "$TERM_PROGRAM" "vscode"
```
To:
```
string match --quiet "$TERM_PROGRAM" "vscode" "kiro"
```

---

## Windows Issues

### Updates Disabled Due to Administrator Installation

If Kiro was installed by an administrator, automatic updates may be disabled. Reinstall Kiro as a regular user to restore automatic updates.

### Unable to Run Scripts

Enable PowerShell execution policy:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### OneDrive Path Issue

If your user profile is stored on OneDrive, Kiro may have difficulty with path resolution. Move your Kiro workspace to a local path (outside OneDrive) to resolve.

---

## MCP Server Connection Issues

### Common Problems

1. **Check server status** — Open the Kiro panel → MCP servers tab → check the connection status indicator
2. **Verify configuration** — Ensure `mcp.json` has valid syntax and the server command/arguments are correct
3. **Check prerequisites** — For the AWS Documentation server, verify Python 3.10+ and `uv` are installed
4. **Review logs** — Output panel → select **"Kiro - MCP Logs"** from the dropdown

### AWS Documentation Server

```bash
# Verify uv installation
uv --version

# Verify Python version (3.10+ required)
python3 --version
```

---

## Getting Help

- [GitHub Issues →](https://github.com/kirodotdev)
- [Official Documentation →](https://kiro.dev/docs/)
