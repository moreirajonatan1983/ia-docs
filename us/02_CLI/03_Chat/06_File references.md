# File References

> **Source:** [kiro.dev/docs/cli/chat/file-references/](https://kiro.dev/docs/cli/chat/file-references/)

---

Include file contents or directory listings inline in your prompts using `@path` syntax.

---

## Basic Usage

Type `@` followed by a file or directory path:

```
@src/index.ts          # Include file contents
@src/                  # Include directory tree
@./relative/path       # Relative paths
@"path with spaces.txt" # Quoted paths (required for spaces)
```

References can appear anywhere in your message:

```
Review @src/auth.ts for security issues
Compare @old.json with @new.json
What's in @src/ that handles authentication?
```

---

## Tab Completion

Press `Tab` after `@` to auto-complete paths:

```
@src/<Tab>           # Shows files in src/
@package<Tab>        # Completes to @package.json
@"Screenshot 2024<Tab>   # Completes to @"Screenshot 2024-01.png"
```

Completion works anywhere in the input line. Quotes are added automatically for paths with spaces.

---

## How References Are Resolved

When a reference could match both a prompt and a file:
1. **Prompts first** — If `@name` matches a prompt from `/prompts list`, it's treated as a prompt
2. **Files second** — Otherwise checked as a file path
3. **Directories third** — If not a file, checked as a directory

Force file resolution: `@./myfile`

---

## File Handling

- **Supported:** Text files (source code, config, markdown) up to **250KB**
- **Not supported:** Binary files (images, executables, archives) — shows an error
- **Large files:** Truncated at 250KB with a warning: `⚠ File 'large-file.json' was truncated`

---

## Directory Trees

`@src/` expands to a tree listing:

```
src/
├── lib/
│   ├── auth.ts
│   └── utils.ts
├── index.ts
└── config.json
```

**Limits:**
- Max depth: 3 levels
- Max items per level: 10 (shows "... (N more items)" if exceeded)
- Ignores: `node_modules`, `.git`, `target`, `dist`, `build`

---

## Examples

```
> Review @src/auth.ts for security issues
> What's different between @v1/handler.py and @v2/handler.py?
> What's the structure of @infra/cdk/?
> Using the config in @serverless.yml, update @src/lambda/index.ts
```

---

## Current Limitations

- Text files up to 250KB only (larger files are truncated)
- Directory trees up to 3 levels deep, 10 items per level
- Explicit paths only — no glob patterns like `@*.ts`
- Full file contents only — no line ranges like `@file.ts:10-20`
- No tilde expansion like `@~/file`
- Binary files are not supported