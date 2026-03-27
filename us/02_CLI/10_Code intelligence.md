# Code Intelligence

> **Source:** [kiro.dev/docs/cli/code-intelligence/](https://kiro.dev/docs/cli/code-intelligence/)

---

Code Intelligence provides deep code understanding using tree-sitter (built-in) and optional LSP integration for symbol search, pattern matching, and codebase exploration — all without leaving your terminal.

---

## Supported Languages

Bash, C, C++, C#, Elixir, Go, Java, JavaScript, Kotlin, Lua, PHP, Python, Ruby, Rust, Scala, Swift, TSX, TypeScript

---

## Built-in Features *(no LSP required)*

| Feature | Description |
|---|---|
| **Symbol search** | Find functions, classes, methods by name (fuzzy matching) |
| **Document symbols** | List all symbols in a file |
| **Symbol lookup** | Look up specific symbols by exact name |
| **Pattern search** | AST-based structural code search |
| **Pattern rewrite** | Automated code transformations using AST patterns |
| **Codebase overview** | High-level codebase structure overview |
| **Codebase map** | Explore directory structure and code organization |

---

## Codebase Overview

Get a complete overview of any workspace in seconds:

```bash
/code overview
```

Focus on a specific directory:
```bash
/code overview ./src/components
```

Use `--silent` for cleaner output when diving deep into a package:
```bash
/code overview --silent
```

Ideal for: onboarding to new codebases, Q&A about project structure, understanding unfamiliar packages quickly.

---

## Documentation Generation

Generate documentation for your codebase with an interactive session:

```bash
/code summary
```

Choose the output format:
- **AGENTS.md** — Documentation for AI agents working with your codebase
- **README.md** — Standard project documentation
- **CONTRIBUTING.md** — Contributor guidelines

---

## Pattern Search & Rewrite

AST-based structural code search and transformation. Find and modify code by structure, not just text.

### Metavariables

Use metavariables (e.g., `$FUNC`, `$ARG`) in patterns to match any expression of that type.

### Pattern Search Examples

```bash
# Find all function calls with specific patterns
/code search "console.log($MSG)"
```

### Pattern Rewrite Examples

```bash
# Replace deprecated API calls
/code rewrite "oldAPI($ARG)" --to "newAPI($ARG)"
```

---

## LSP Integration *(Optional)*

The built-in tree-sitter features work out of the box. Run `/code init` only if you want enhanced LSP features.

> Code intelligence is configured per workspace — each project maintains its own LSP settings independently.

```bash
/code init
```

**Additional LSP-powered operations:**

| Feature | Description |
|---|---|
| **Find references** | Locate all usages of a symbol at a position |
| **Go to definition** | Navigate to where a symbol is defined |
| **Rename symbol** | Rename symbols across the codebase |
| **Get diagnostics** | Get errors and warnings for a file |
| **Hover documentation** | Get type information and documentation at position |
| **Completions** | Get completion suggestions at position |

---

## Slash Commands

| Command | Description |
|---|---|
| `/code init` | Initialize LSP for the current workspace |
| `/code init -f` | Force re-initialize LSP |
| `/code status` | Show current LSP connection status |
| `/code logs` | View LSP diagnostic logs |
