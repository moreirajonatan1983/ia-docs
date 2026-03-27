# Bugfix Specs

> **Source:** [kiro.dev/docs/specs/bugfix-specs/](https://kiro.dev/docs/specs/bugfix-specs/)

---

Bugfix Specs provide a structured approach for systematically diagnosing and fixing bugs with surgical precision while preventing regressions.

---

## Key Benefits

| Benefit | Description |
|---|---|
| **Surgical fixes** | Explicit constraints ensure only necessary changes are made |
| **Regression prevention** | Unchanged behavior is documented and tested |
| **Documentation** | Complete record of the bug, fix, and reasoning for future reference |
| **Reliability** | Structured workflow prevents common pitfalls of ad-hoc fixes |

---

## When to Use Bugfix Specs

Best for:
- Complex bugs requiring root cause analysis
- Bugs in critical code paths where regressions are costly
- Bugs that need documentation for compliance or team knowledge
- Situations where previous fix attempts caused regressions

---

## How It Works

Bugfix Specs follow the same three-phase workflow as Feature Specs (Requirements → Design → Tasks), but with content tailored for surgical bug fixes:

### 1. Bugfix Analysis Phase

Instead of a requirements document, you create a `bugfix.md` that captures:

```
Current Behavior (Defect)
- WHEN [condition] THEN the system [incorrect behavior]

Expected Behavior (Correct)
- WHEN [condition] THEN the system SHALL [correct behavior]

Unchanged Behavior (Regression Prevention)
- WHEN [condition] THEN the system SHALL CONTINUE TO [existing behavior]
```

This explicit structure ensures Kiro understands not just what's broken, but what must remain working.

### 2. Design Phase

Kiro explores the codebase to root cause the issue and generates a `design.md` with:
- Root cause analysis
- Proposed fix approach
- Properties to test for:
  - Current implementation produces incorrect behavior *(validates the bug exists)*
  - Fixed implementation produces correct behavior *(validates the fix works)*
  - Unchanged implementation continues working *(prevents regressions)*

### 3. Tasks Phase

Implementation tasks are generated with [property-based tests (PBTs)](https://kiro.dev/docs/specs/correctness) that validate:
- The bug is reproducible
- The bug is fixed
- No regressions are introduced

---

## Getting Started

1. Choose **Spec** from the chat pane.
2. Describe the bug, including:
   - When the bug occurs (reproduction steps)
   - What should happen instead
   - Any constraints (code that shouldn't be modified)
3. Choose **Bugfix** when Kiro asks what your intent is.
4. Follow the workflow through analysis, design, and implementation.

---

## Learn More

- [Best Practices for Bugfix Specs →](https://kiro.dev/docs/specs/best-practices/#bugfix-specs)
- [Correctness with Property-based Tests →](https://kiro.dev/docs/specs/correctness/)