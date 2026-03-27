# Guides

> **Source:** [kiro.dev/docs/guides/](https://kiro.dev/docs/guides/)

---

Official step-by-step follow-along guides for learning Kiro through practical scenarios.

---

## Available Guides

| Guide | Description |
|---|---|
| [Learn by Playing →](https://kiro.dev/docs/guides/learn-by-playing/) | Build a real game project while learning Kiro's powerful features through hands-on interactive tutorials |
| [Language Support →](https://kiro.dev/docs/guides/languages-and-frameworks/) | Framework-specific guides for React, Python, Go, and more to help you get the most out of Kiro with your tech stack |
| [Migrating from VS Code →](https://kiro.dev/docs/guides/migrating-from-vscode/) | Seamlessly transition from VS Code to Kiro with one-click migration including all your extensions and settings |

---

## Migrating from VS Code

Kiro's VS Code foundation enables complete compatibility with your development environment. You can transfer your personalized setup — extensions, themes, configurations, and shortcuts — with no compatibility concerns.

### Profile Migration

1. Open the Command Palette: `Cmd+Shift+P` (Mac) / `Ctrl+Shift+P` (Windows/Linux)
2. Search for **"Import Profile from VS Code"**
3. Kiro will automatically detect and import your VS Code profiles

#### Manual Profile Migration

If automatic migration doesn't work:
1. In VS Code: `Cmd+Shift+P` → "Profiles: Export Profile" → save as `.code-profile`
2. In Kiro: `Cmd+Shift+P` → "Profiles: Import Profile" → select the file

### Settings and Interface

| Item | How to Access |
|---|---|
| **Kiro Settings** | `Cmd/Ctrl+Shift+P` → "Preferences: Open Settings (UI)" → navigate to Kiro Agent section |
| **VS Code Settings** | Same Command Palette path — your existing VS Code preferences remain fully functional |

Kiro extends VS Code's settings architecture with dedicated controls for:
- AI behaviors and agent automation
- Trusted commands
- Kiro-exclusive features (steering, specs, hooks)

### Version Updates

Kiro stays synchronized with VS Code's development cycle through regular rebasing. We incorporate the latest features while selecting stable VS Code releases to ensure reliability alongside AI enhancements.

### Extension Compatibility

Kiro uses the **OpenVSX extension registry**. Extensions available in OpenVSX migrate seamlessly:

| Extension Type | Compatibility |
|---|---|
| Language extensions | Full functionality for OpenVSX-available extensions |
| Theme extensions | Complete visual compatibility |
| Debugging extensions | Uninterrupted debugging workflows for compatible extensions |
| Git extensions | Augmented with intelligent commit generation and automated code review |

> ⚠️ Only extensions available in the **OpenVSX registry** can be imported. Some VS Code Marketplace exclusives may not be available in Kiro.
