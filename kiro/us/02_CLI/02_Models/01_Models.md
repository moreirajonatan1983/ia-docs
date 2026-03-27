# Models — Kiro CLI

> **Source:** [kiro.dev/docs/cli/models/](https://kiro.dev/docs/cli/models/)

---

Kiro CLI supports the same models as the IDE. Refer to the [IDE Models page](../../01_IDE/02_Models.md) for the complete model details, comparison table, behavioral differences, and best practices.

---

## Quick Comparison

Cost is relative to **Auto (1.0x baseline)**. For example, a task that costs 10 credits on Auto would cost 22 credits on Opus, 4 credits on Haiku, or 0.5 credits on Qwen3 Coder Next.

| Model | Best For | Cost |
|---|---|---|
| **Auto** *(recommended)* | General use, best quality/cost ratio | 1.0x |
| **Claude Opus 4.6** | Complex agentic coding, large codebases | ~2.2x |
| **Claude Sonnet 4.6** | Iterative dev workflows, multi-model pipelines | ~1.0x |
| **Claude Haiku 4.5** | Fast iterations, credit conservation | ~0.4x |
| **MiniMax M2.5** | Full dev lifecycle at low cost | 0.25x |
| **DeepSeek 3.2** | Agentic workflows, code generation | 0.25x |
| **MiniMax M2.1** | Multilingual programming, UI generation | 0.15x |
| **Qwen3 Coder Next** | — | 0.5x |

---

## How to Switch Models

### From the chat interface

Use the model dropdown in the chat interface. If a model doesn't appear, restart the client.

### From the command line

Set a specific model as default:
```bash
kiro-cli settings chat.defaultModel claude-opus4.6
```

Save the **current** model as default for all future sessions (from within a chat session):
```
> /model set-current-as-default
```

This stores your preference in `~/.kiro/settings/cli.json`. New sessions automatically use this model.