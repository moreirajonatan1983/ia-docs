# Correctness with Property-based Tests

> **Source:** [kiro.dev/docs/specs/correctness/](https://kiro.dev/docs/specs/correctness/)

---

Kiro uses property-based testing (PBT) to validate that your implementation actually matches what you defined in your specs. This approach generates hundreds or thousands of test cases automatically, catching edge cases you'd never write manually.

---

## Concepts

### What is a property?

A property is a **universal statement** about how your system should behave. Properties express the invariants and contracts that should always be true in your system, regardless of the specific data involved.

> *"For any authenticated user and any active listing, the user can view that listing."*

This captures a general rule about system behavior that must hold across all valid scenarios. In the Kiro specification world, this maps directly to EARS requirements.

### How property-based testing works

**Traditional test:**
- User adds Car #5 to favorites → Car #5 appears in their list

**Property-based test:**
- WHEN any user adds any car to favorites, THE System SHALL display it in their list

PBT automatically tests this with:
- User A adding Car #1
- User B adding Car #500
- Users with special characters in names
- Cars with various statuses
- Hundreds more combinations

This catches edge cases and verifies implementation matches intent.

Throughout this process, PBT probes to find counter-examples through **"shrinking"** — almost like a red team trying to break your code. When it finds violations, Kiro can automatically update your implementation or surface options to fix the spec, implementation, or test itself.

---

## Property-based Testing with Specs

### Workflow

Kiro extracts properties from your EARS-formatted requirements:

1. Identifies requirements like *"THE System SHALL allow authenticated users to view active car listings"*
2. Determines which properties can be logically tested
3. Generates hundreds or thousands of random test cases when you choose to run them

### Design Phase

In the design phase, Kiro:
- Extracts properties from your requirements
- Generates test cases
- Hovering over a property reveals its connection to the original requirement and linked task

### Executing Tasks

In the execution phase, Kiro runs the generated PBT cases against your implementation.

> **Note:** PBTs are **optional by default** so you can focus on your core implementation first. Once a property test runs, you can see the reference to the generated code.

When a property test fails, Kiro:
1. Identifies the specific failure scenario and surfaces it for review
2. Allows you to chat with Kiro to understand the failure
3. Lets you determine the appropriate fix — whether updating the implementation, adjusting the test, or refining the requirement itself