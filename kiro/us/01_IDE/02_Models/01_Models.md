# Models

> **Source:** [kiro.dev/docs/models/](https://kiro.dev/docs/models/)

---

Kiro supports multiple AI models. You can switch models from the chat interface dropdown — your selection applies to all subsequent messages in the conversation.

---

## Quick Comparison

Cost is relative to **Auto (1.0x baseline)**. For example, a task that costs 10 credits on Auto would cost 22 credits on Opus, 4 credits on Haiku, or 0.5 credits on Qwen3 Coder Next.

| Model | Best For | Cost Multiplier |
|---|---|---|
| **Auto** *(recommended)* | General use, best quality/cost ratio | 1.0x |
| **Claude Opus 4.6** | Complex agentic coding, debugging, large codebases | ~2.2x |
| **Claude Opus 4.5** | Advanced reasoning, sophisticated challenges | ~2.2x |
| **Claude Sonnet 4.6** | Iterative dev workflows, multi-model pipelines | ~1.0x |
| **Claude Sonnet 4.5** | Complex agents, extended autonomous operation | ~1.0x |
| **Claude Sonnet 4.0** | Consistent, predictable model selection | ~1.0x |
| **Claude Haiku 4.5** | Fast iterations, simple fixes, credit saving | ~0.4x |
| **MiniMax M2.5** | Full dev lifecycle, code review | 0.25x |
| **DeepSeek 3.2** | Agentic workflows, code generation | 0.25x |
| **MiniMax M2.1** | Multilingual programming, UI generation | 0.15x |
| **Qwen3 Coder Next** | — | 0.5x |

---

## Model Details

### Auto *(recommended)*

Kiro's model router. Auto combines multiple frontier models with optimization techniques to deliver the best quality-to-cost ratio. It automatically chooses the optimal model for each task and delivers Sonnet 4-class results. Auto uses best-in-class LLM models (Claude Sonnet 4 and similar) and maintains a high quality bar to ensure results compare to or exceed the individual models available to you.

---

### Claude Opus 4.6

Anthropic's most capable model with state-of-the-art coding and agentic performance. Top scores on Terminal-Bench 2.0 and SWE-bench Verified for agentic coding. Stays productive over longer sessions without context drift and handles multi-million-line codebases, planning upfront and adapting as needed. Improved debugging and code review capabilities let it catch its own mistakes, and it thinks more carefully on complex problems, revisiting reasoning before committing. [Learn more →](https://www.anthropic.com/research/claude-opus-4-6)

---

### Claude Opus 4.5

Anthropic's most intelligent model, combining maximum capability with practical performance. Significant improvements in reasoning, coding, and problem-solving at a more accessible price point than previous Opus models. Handles tradeoffs and ambiguity well across multiple systems, making it suited for the most sophisticated software development challenges. [Learn more →](https://www.anthropic.com/news/claude-opus-4-5)

---

### Claude Sonnet 4.6

A full upgrade from Sonnet 4.5 that approaches Opus 4.6 intelligence while being more token efficient. Excels at iterative development workflows and maintains context across long sessions. Handles both lead agent and subagent roles in multi-model pipelines, making it well-suited for teams using Kiro powers and custom subagents. [Learn more →](https://www.anthropic.com/news/claude-sonnet-4-6)

---

### Claude Sonnet 4.5

Anthropic's best model for complex agents and coding, with the highest intelligence across most tasks. State-of-the-art on SWE-bench Verified with extended autonomous operation for hours with effective tool usage. Improved planning, system design, and security engineering. [Learn more →](https://www.anthropic.com/news/claude-sonnet-4-5)

---

### Claude Sonnet 4.0

Direct access to Anthropic's Claude Sonnet 4.0 for users who prefer consistent model selection. Same model for all interactions with no routing or optimization layers. Full control and complete transparency, with predictable behavior for workflows that depend on specific model characteristics. [Learn more →](https://www.anthropic.com/news/claude-4)

---

### Claude Haiku 4.5

Anthropic's fastest model with near-frontier performance. Matches Sonnet 4 performance across reasoning and coding at more than twice the speed. Near-frontier intelligence at one-third the cost, and the first Haiku model with extended thinking capabilities. [Learn more →](https://www.anthropic.com/news/claude-haiku-4-5)

---

### MiniMax M2.5

Open weight model that matches frontier-class coding performance at a fraction of the cost. Trained with reinforcement learning across hundreds of thousands of real-world environments, delivering strong results across the full development lifecycle from system design to code review. **0.25x credit multiplier** with inference running in US East (N. Virginia). [Learn more →](https://www.minimax.io/news/minimax-m25)

---

### DeepSeek 3.2

Open weight model best suited for agentic workflows and code generation. Handles long tool-calling chains, stateful sessions, and multi-step reasoning well. **0.25x credit multiplier** with inference running in US East (N. Virginia). [Learn more →](https://api-docs.deepseek.com/news/news250325)

---

### MiniMax M2.1

Open weight model best suited for multilingual programming and UI generation. Delivers strong results across Rust, Go, C++, Kotlin, TypeScript, and others. **0.15x credit multiplier** with inference running in US East (N. Virginia) and EU (Frankfurt). [Learn more →](https://minimax.io/news/minimax-m21)

---

## How Models Behave Differently

Not all models work the same way. Understanding these differences helps you pick the right one:

- **Planning depth:** Opus models think longer before acting. They plan multi-step approaches, consider edge cases, and revisit their reasoning. Sonnet and Haiku are more direct: they start working sooner and iterate faster.
- **Self-correction:** Opus 4.6 in particular is better at catching its own mistakes during code review and debugging. If you're seeing bugs in generated code, switching to Opus can help.
- **Session endurance:** For long-running tasks (like working through a spec), Opus models maintain focus better over extended sessions. Haiku and Sonnet are better suited for shorter, focused interactions.
- **Initiative level:** Opus models tend to take more initiative, making broader changes when they see opportunities. Sonnet is more conservative and sticks closer to what you asked for. Choose based on whether you want the model to lead or follow.

---

## Model Lifecycle

Models in Kiro go through two stages. Each stage reflects the model's maturity and the level of support you can expect.

> **Note:** Inference requests for **experimental models** may be processed across multiple AWS Regions globally to optimize availability and performance. See [data protection](https://kiro.dev/docs/privacy-and-security/data-protection/#global-cross-region-inference-for-experimental-features) for details on cross-region inference.

---

## Best Practices

- **Start with Auto** for most work. It optimizes both quality and cost automatically.
- **Switch to Opus** when you hit a wall on a complex problem or need sustained multi-file work.
- **Use Haiku** for quick iterations, simple fixes, or when you want to conserve credits.
- **Monitor your usage** in your [account settings](https://kiro.dev/docs/billing/) to understand how model choice affects consumption.
- **Factor model cost into your tier:** If you primarily use Opus, consider Pro+ or Power for more credits. See [plans and billing](https://kiro.dev/docs/billing/) for details.