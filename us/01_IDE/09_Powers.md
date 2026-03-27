# Powers

> **Source:** [kiro.dev/docs/powers/](https://kiro.dev/docs/powers/)

---

Powers are dynamic bundles of context and MCP tools that give your AI agent instant expertise for any framework or tool — loading only what's relevant, only when it's needed.

---

## Get Started

- [Explore Powers](https://kiro.dev/powers) — Browse curated powers from launch partners and install with one click
- [Install a Power →](https://kiro.dev/docs/powers/installation/)
- [Create a Power →](https://kiro.dev/docs/powers/create/)

---

## Concept

### The Problem: Context Overload

AI agents face two opposing challenges:

**Without framework context, agents guess.**
Your agent can call Stripe APIs, but does it know to use idempotent keys? It can query Neon, but does it understand connection pooling for serverless? Without built-in expertise, you're both manually reading documentation and refining approaches until the output is right.

**With too much context, agents slow down.**
Connect five MCP servers and your agent loads 100+ tool definitions before writing a single line of code. Five servers might consume 50,000+ tokens — 40% of your context window — before your first prompt. More tools should mean better results, but unstructured context overwhelms the agent, leading to slower responses and lower quality output.

---

### How Powers Work

Instead of loading all MCP tools at once, powers **activate dynamically based on keywords** in your conversation.

When you start a task, Kiro:
1. Reads the task description
2. Evaluates installed powers against the task
3. Loads **only relevant powers** into context

When you mention "payment" or "checkout," the Stripe power activates — loading Stripe's MCP tools and POWER.md steering into context. When you move to database work, the Supabase power activates and Stripe deactivates.

---

### What's in a Power?

A power is a unified bundle that includes:

| Component | Description |
|---|---|
| `POWER.md` | Steering file that tells the agent what MCP tools it has available and when to use them |
| **MCP server configuration** | Tools and connection details for the MCP server |
| **Steering/hooks** *(optional)* | Automated tasks that run on IDE events or via slash commands |

---

### What Makes Powers Different

| Feature | Description |
|---|---|
| **Dynamic MCP tool loading** | Traditional MCP servers load all tools upfront. Powers load tools on-demand, reducing baseline context usage while giving your agent access to dozens of technologies |
| **Open ecosystem** | Browse curated powers from launch partners including Datadog, Dynatrace, Figma, Neon, Netlify, Postman, Supabase, Stripe, Strands SDK, and AWS Aurora. Install community-built powers from GitHub URLs, or create and share your own |
| **One-click install** | Browse powers directly in Kiro or on kiro.dev. Click "Install" and the power registers automatically. No JSON configuration files, no command-line setup |

---

## Launch Partner Powers

| Partner | Use Case |
|---|---|
| **Stripe** | Payments, subscriptions, billing |
| **Supabase** | PostgreSQL database, auth, storage |
| **Neon** | Serverless PostgreSQL |
| **Figma** | Design tokens, component specs |
| **AWS Aurora** | Managed relational database |
| **Netlify** | Frontend deployment, edge functions |
| **Postman** | API testing and documentation |
| **Datadog** | Monitoring, logs, APM |
| **Dynatrace** | Observability platform |
| **Strands SDK** | Agent development |
