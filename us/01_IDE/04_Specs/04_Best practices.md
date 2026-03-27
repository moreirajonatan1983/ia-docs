# Best Practices — Specs

> **Source:** [kiro.dev/docs/specs/best-practices/](https://kiro.dev/docs/specs/best-practices/)

---

## Feature Specs

### Which workflow should I choose?

Feature Specs support two workflows: **Requirements-First** and **Design-First**.

| Choose Requirements-First when... | Choose Design-First when... |
|---|---|
| You know the behavior of the system you want to build | You have an existing technical design or architecture |
| Architecture is flexible and can be designed to meet needs | System must meet strict non-functional requirements |
| Building product features driven by customer feedback | Prototyping with a specific tech stack |
| Starting without technical constraints | Exploring technical feasibility before committing to scope |

### Can I switch workflows after starting a spec?

No, you must choose a workflow when creating the spec. If you need to change approaches, create a new Feature Spec with the desired workflow. You can copy relevant content from the previous spec if needed.

### Can I use both workflows for the same project?

Yes! You can create multiple specs. For example:
1. Use Design-First to validate technical feasibility
2. Create a Requirements-First spec for full feature development

### How do I import existing designs or architecture?

- **Using Design-First workflow:** Create a new Feature Spec and select Design-First, upload architecture diagrams (PNG, JPG) or paste design content, Kiro will formalize the design into `design.md`.
- **Using images:** Export diagrams from tools like draw.io, Lucidchart, or take photos of whiteboard sketches and include them in your initial prompt.
- **Using MCP integration:** If your design tool has an [MCP server](https://kiro.dev/docs/mcp), you can connect directly to import designs.

### How do I import existing requirements?

- **Using MCP integration:** If your requirements tool has an MCP server (JIRA, Confluence, etc.), connect directly to import requirements into your spec session.
- **Manual import:** Copy your existing requirements into a new file in your repo and open a spec chat session:
  ```
  #foo-prfaq.md Generate a spec from it
  ```

### How do I iterate on my Feature Specs?

Continue the spec chat session to refine requirements, update the design, or adjust tasks. Kiro maintains the context of your specification throughout the conversation.

---

## Bugfix Specs

### How do I write a good bug description?

A clear bug description helps Kiro perform accurate root cause analysis. Include:

1. **Reproduction steps** — Describe the exact conditions that trigger the bug
2. **Current behavior** — What the system does now (the defect)
3. **Expected behavior** — What the system should do instead
4. **Constraints** — Any code or behavior that must not change

**Example prompt:**
```
When a user submits a form with special characters in the name field (e.g., O'Brien),
the API returns a 500 error. It should accept the input and save it correctly.
The validation logic for email and password fields should not be affected.
```

### How do I prevent regressions with Bugfix Specs?

Bugfix Specs explicitly capture "unchanged behavior" alongside the fix. During the analysis phase, document what must continue working:

```
- WHEN [condition] THEN the system SHALL CONTINUE TO [existing behavior]
```

Kiro generates property-based tests that validate both the fix and the preservation of existing behavior.

### When should I use a Bugfix Spec vs. a quick fix?

**Use a Bugfix Spec when:**
- The bug is in a critical code path
- Previous fix attempts caused regressions
- The root cause isn't immediately obvious
- You need documentation for compliance or team knowledge

**A quick fix in chat is fine for:** typos, simple logic errors, or well-understood one-line changes.

### Can I convert a Bugfix Spec into a Feature Spec?

Not directly. If root cause analysis reveals that the fix requires significant new functionality, create a separate Feature Spec and keep the Bugfix Spec focused on the original defect.

---

## General

### How do I share specs with my team?

Specs are designed to be version-controlled. Store specs directly in your project repository alongside the code they describe. This keeps all project artifacts together and maintains the connection between requirements and implementation.

### Can I share specs across multiple teams?

Yes, by leveraging Git submodules or package references:
1. Create a central specs repository
2. Use Git submodules or package references to link specs to individual projects
3. Implement cross-repository workflows for proposing, reviewing, and updating shared specs

### Can I start a spec session from a vibe session?

Yes. In a vibe conversation, say `Generate spec`. Kiro will ask if you want to start a spec session and will generate requirements based on the context of your vibe session.

### Can I execute all the tasks in my spec in a single shot?

Yes. Click the **"Run all tasks"** button in your `tasks.md` file. Note: this will only run incomplete tasks that are marked as required.

### What if some tasks are already implemented?

**Option 1:** Click **"Update tasks"** in your `tasks.md` file — Kiro will automatically mark completed tasks.

**Option 2:** In a spec session, ask Kiro: *"Check which tasks are already complete"* — Kiro will analyze your codebase and mark completed tasks.

### How do I reference a spec in chat?

Use the `#spec` context provider. Type `#spec` and press Enter to see a list of available specs, then select the one you want to include. Kiro automatically includes all spec files (`requirements.md`, `design.md`, and `tasks.md`) in the conversation context.

### How many specs can I have in a single repo?

There is no hard limit. Organize specs logically within `.kiro/specs/` using descriptive names for each feature or bugfix.