# Specs

> **Source:** [kiro.dev/docs/specs/](https://kiro.dev/docs/specs/)

---

Specs or specifications are structured artifacts that formalize the development process for features and bug fixes in your application. They provide a systematic approach to transform high-level ideas into detailed implementation plans with clear tracking and accountability.

With Kiro's specs, you can:
- Break down requirements into user stories with acceptance criteria
- Build design docs with sequence diagrams and architecture plans
- Track implementation progress across discrete tasks
- Collaborate effectively between product and engineering teams

---

## Core Structure

Every spec generates three key files:

- **requirements.md** (or **bugfix.md**) — Captures user stories, acceptance criteria, or bug analysis in structured notation.
- **design.md** — Documents technical architecture, sequence diagrams, and implementation considerations.
- **tasks.md** — Provides a detailed implementation plan with discrete, trackable tasks.

---

## Three-Phase Workflow

All specs follow a three-phase workflow:

**1. Requirements or Bug Analysis** — Define what needs to be built or fixed
- Feature Specs: User stories and acceptance criteria in `requirements.md`
- Bugfix Specs: Bug analysis with current/expected/unchanged behavior in `bugfix.md`

**2. Design** — Create technical architecture and implementation approach in `design.md`
- System architecture and component design
- Sequence diagrams and data flow
- Error handling and testing strategy

**3. Tasks** — Generate discrete, executable implementation tasks in `tasks.md`
- Trackable tasks with clear outcomes
- Real-time status updates as you implement
- Run tasks individually or all at once

---

## Task Execution

Kiro provides a task execution interface for `tasks.md` files that displays real-time status updates. Tasks are updated as in-progress or completed, allowing you to efficiently track implementation progress.

---

## Types of Specs

### Feature Specs
For building new features and capabilities in your application. Feature Specs guide you through requirements gathering, technical design, and implementation planning.

### Bugfix Specs
For systematically diagnosing and fixing bugs with surgical precision while preventing regressions. Bugfix Specs help you identify root causes, design fixes, and validate that nothing else breaks.

---

## Getting Started

1. From the Kiro pane, click the **+** button under Specs. Alternatively, choose **Spec** from the chat pane.
2. Kiro will ask if you are developing a **Feature** or fixing a **Bug**
   - If you choose **Feature**, describe your feature and choose your workflow: Requirements-First or Design-First
   - If you choose **Bug**, describe your bug
3. Follow the workflow through each phase to implementation

---

## When to Use Specs vs Vibe

**Use Specs when:**
- Building complex features requiring structured planning.
- Fixing bugs where regressions are costly.
- You need documentation for team collaboration.
- Requirements or design need iteration.

**Use Vibe when:**
- Quick exploratory coding.
- Prototyping without clear goals.

---

## Learn More

- [Feature Specs →](https://kiro.dev/docs/specs/feature-specs/)
- [Bugfix Specs →](https://kiro.dev/docs/specs/bugfix-specs/)
- [Best Practices →](https://kiro.dev/docs/specs/best-practices/)