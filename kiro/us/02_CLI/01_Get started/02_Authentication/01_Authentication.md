# Authentication Methods — Kiro CLI

> **Source:** [kiro.dev/docs/cli/authentication/](https://kiro.dev/docs/cli/authentication/)

---

## Sign In to Kiro CLI

1. At the command line, enter `kiro-cli` or `kiro-cli login`. You'll be prompted to press Enter to complete sign-in in your browser.

2. In your browser, choose the organization or system through which you will authenticate:
   - Google
   - GitHub
   - Builder ID
   - Your organization — including AWS GovCloud (US)

3. After you authenticate, you'll receive a message in your browser directing you back to your terminal.

4. When you return to your terminal, you should be signed in with the Kiro CLI.

> **Note:** Individual login methods such as GitHub, Google, and AWS Builder ID are **not available** in AWS GovCloud (US) regions.
>
> Users know they will be using Kiro with AWS GovCloud (US) by ensuring the Start URL used during authentication contains `"us-gov-home"`, for example:
> ```
> https://start.us-gov-home.awsapps.com/directory/d-XXXXXXXXXX
> ```
>
> **Kiro IDE version 0.9.2+** and **Kiro CLI version 1.25.0+** are required for AWS GovCloud (US) regions support.

---

## Sign In from a Remote Machine

When running Kiro CLI on a remote machine (via SSH, SSM, containers, etc.), authentication works differently since the remote machine cannot open a browser.

- **For Builder ID and IAM Identity Center:** Kiro CLI uses **device code authentication**. You'll see a URL and code to enter in your local browser — no additional setup required.
- **For social login (Google or GitHub):** The CLI uses PKCE authentication which requires **port forwarding**. The OAuth callback redirects to `localhost`, which won't reach the remote CLI without a tunnel.

**To sign in with social login on a remote machine:**

1. Run `kiro-cli login` and select *"Use for Free with Google or GitHub"*
2. Note the port number displayed (it varies each time, e.g., `49153`)
3. In a new terminal on your **local machine**, set up port forwarding:
   ```bash
   ssh -L <PORT>:localhost:<PORT> -N user@remote-host
   ```
   Replace `<PORT>` with the port from step 2, and `user@remote-host` with your remote credentials.
4. Press Enter in the CLI, then open the URL in your local browser
5. Complete authentication — the callback reaches the CLI through the tunnel

**SSH port forwarding examples:**

```bash
# Basic port forwarding (replace 49153 with your actual port)
ssh -L 49153:localhost:49153 -N user@remote-host

# With a custom identity file (common for EC2)
ssh -i ~/.ssh/my-key.pem -L 49153:localhost:49153 -N user@remote-host

# Using an SSH config alias
ssh -L 49153:localhost:49153 -N myserver
```

**Troubleshooting port forwarding:**

| Issue | Solution |
|---|---|
| Authentication timed out | Port forwarding isn't active or wrong port. Verify port matches CLI output. |
| Failed to bind callback port | Port is in use on remote. Run `lsof -i :<PORT>` to identify the process. |
| Address already in use (SSH) | Port is in use locally. Close other tunnels or stale SSH sessions. |
| Tunnel disconnects mid-auth | Keep SSH terminal open until auth completes. Add `-o ServerAliveInterval=60` |

---

## Sign Out of Kiro CLI

```bash
kiro-cli logout
```

---

## Troubleshooting Authentication Issues

If you encounter problems during the authentication process, such as browser redirect failures or sign-in errors, check our [troubleshooting guide](https://kiro.dev/docs/troubleshooting/#authentication-issues) for platform-specific solutions and common fixes.

---

## Next Steps

- [Review FAQ →](https://kiro.dev/faq)
- [Explore Chat features →](https://kiro.dev/docs/cli/chat)
- [Get started with Kiro CLI →](https://kiro.dev/docs/cli)