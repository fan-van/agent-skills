---
name: code-understanding
description: Human-first coding workflow for Codex. Use when creating, modifying, refactoring, debugging, reviewing, or explaining code. Enforces human readability, human ownership, controlled abstraction, meaningful comments, change-impact analysis, verification, and a final change report. The goal is code that a human can understand, verify, modify, and own—not merely code that works.
---

# Code Understanding v2

## Core Principle

Code is not finished when it works.

Code is finished when a human can:

1. understand what it does,
2. understand why it exists,
3. verify that it is correct,
4. modify it safely,
5. identify its impact,
6. take ownership of it later.

Prefer the simplest design that correctly solves the current problem.

## Workflow

For every non-trivial coding task, follow this lifecycle:

1. Human-First
2. Understand
3. Plan
4. Implement
5. Verify
6. Human Readability Gate
7. Human Ownership Mode
8. Abstraction Control
9. Comment Enforcement
10. Change Impact Analysis
11. Final Change Report

For trivial changes, do not create unnecessary ceremony. Still apply the relevant gates before finishing.

## 01 — Human-First

Before changing code, determine:

- What is the user-visible or business outcome?
- What problem is actually being solved?
- What must remain unchanged?
- What is the smallest reasonable change?
- What would make the resulting code difficult for a human to maintain?

Do not optimize for cleverness, abstraction, or future extensibility unless the task requires it.

When requirements are ambiguous, inspect the repository and existing conventions before inventing new architecture.

## 02 — Understand

Inspect enough of the repository to understand the relevant behavior.

Identify:

- entry point,
- relevant files,
- call flow,
- data flow,
- state changes,
- external dependencies,
- persistence/network/device boundaries,
- error paths,
- tests,
- configuration,
- generated code if relevant.

Do not claim to understand a file based only on its filename.

Prefer repository evidence over assumptions.

For a change spanning multiple files, build a concise mental model:

```text
Entry
  ↓
Orchestration
  ↓
Business rule
  ↓
Side effect
  ↓
Result / state update
```

If the flow is different, describe the actual flow.

## 03 — Plan

Before implementation, decide:

- which files need to change,
- why each file needs to change,
- what behavior changes,
- what behavior must not change,
- what risks exist,
- how the change will be verified.

Prefer modifying existing code over introducing new layers.

Do not create a new abstraction merely because one could exist.

For substantial changes, establish a short implementation plan before editing.

## 04 — Implement

Implement the smallest coherent change.

Rules:

- preserve existing architecture unless there is a concrete reason to change it,
- preserve naming and local conventions,
- avoid unrelated cleanup,
- avoid opportunistic refactors,
- avoid speculative extensibility,
- keep functions and classes understandable,
- keep control flow explicit when explicitness improves comprehension,
- avoid hiding important business behavior behind generic helpers.

If an abstraction is introduced, it must have a concrete justification.

## 05 — Verify

Verification must match the change.

Possible checks include:

- formatter,
- linter,
- type checker,
- compiler,
- unit tests,
- integration tests,
- targeted runtime checks,
- existing project validation commands.

Do not report a check as passed unless it was actually performed.

If a check could not be performed, say so.

Separate:

- verified,
- not verified,
- blocked,
- unrelated pre-existing failure.

Never silently treat an unverified assumption as a successful verification.

## 06 — Human Readability Gate

Before declaring completion, inspect the changed code as if you were a developer returning to it six months later.

Ask:

### Intent
- Can I tell what this code is trying to accomplish?
- Is the business rule visible?
- Is important control flow easy to follow?

### Naming
- Do names describe meaning rather than implementation mechanics?
- Are abbreviations understandable?
- Could a human infer the role of each important variable/function/class?

### Structure
- Is the code split into reasonable units?
- Is the nesting excessive?
- Is there unnecessary indirection?
- Is the simplest path visible?

### Cognitive load
- Does understanding this function require jumping across many files?
- Are there too many wrappers?
- Are there too many generic helpers?
- Does the reader need to understand framework machinery before understanding business logic?

### Readability verdict

Classify the result:

- PASS — understandable without unusual effort.
- PASS WITH NOTE — understandable, but a specific area deserves attention.
- FAIL — working code is still too difficult for a human to maintain.

If FAIL, simplify before finishing.

See `references/human-readability.md`.

## 07 — Human Ownership Mode

The final code must be maintainable by a human without relying on the original AI conversation.

For the changed behavior, identify:

- where the feature starts,
- where the main decision is made,
- where important state changes,
- where side effects occur,
- what assumptions must remain true,
- what should be changed if requirements change,
- what must be tested after modification.

A future developer should be able to answer:

```text
Where do I start?
What controls the behavior?
Why is it written this way?
What can I safely change?
What must I verify afterward?
```

If these answers are not apparent from the code and concise documentation, improve the implementation or add targeted documentation.

See `references/human-ownership.md`.

## 08 — Abstraction Control

Actively look for unnecessary abstraction.

Flag newly introduced:

- interfaces,
- abstract classes,
- factories,
- providers,
- managers,
- coordinators,
- contexts,
- adapters,
- strategies,
- wrappers,
- generic utilities,
- indirection layers.

For each new abstraction, answer:

1. What concrete problem does it solve now?
2. What existing code could be simpler without it?
3. Does it reduce duplication or complexity?
4. Does it isolate a real boundary?
5. Does the project already use this pattern?
6. Is the abstraction worth the cognitive cost?

Reject an abstraction whose only justification is:

- "better architecture",
- "future extensibility",
- "clean code",
- "SOLID",
- "best practice",
- "separation of concerns"

unless a concrete current requirement supports it.

Prefer:

```text
simple code
    >
unnecessary abstraction
```

See `references/abstraction-control.md`.

## 09 — Comment Enforcement

Comments must explain information that code cannot express clearly.

Good comments explain:

- WHY a decision exists,
- business constraints,
- non-obvious invariants,
- external system behavior,
- compatibility constraints,
- safety constraints,
- timing/order requirements,
- intentionally unusual code.

Bad comments merely translate code:

```text
// Increment count
count++;
```

Do not add comments that become false after trivial refactoring.

Prefer meaningful comments such as:

```text
// Keep initialization in the same execution context as runApp.
// Flutter reports a Zone mismatch if binding initialization occurs
// in a different Zone.
```

Comment rules:

- explain WHY, not WHAT,
- keep comments close to the behavior they explain,
- remove stale comments,
- do not comment every line,
- do not use comments to compensate for confusing code when the code itself can be simplified.

See `references/comment-enforcement.md`.

## 10 — Change Impact Analysis

After implementation, determine the actual impact.

Separate:

### Direct changes
Files/functions/classes explicitly modified.

### Behavioral impact
What user-visible or business behavior can change?

### Indirect impact
Callers, consumers, state, persistence, network/device communication, configuration, or tests affected by the changed behavior.

### Risk
Potential regressions or assumptions.

### Validation coverage
What was actually tested and what remains unverified?

Use this model:

```text
Changed code
    ↓
Direct callers
    ↓
State / data flow
    ↓
External side effects
    ↓
User-visible behavior
```

Do not claim an indirect impact unless repository evidence supports it.

See `references/change-impact.md`.

## 11 — Final Change Report

Every non-trivial coding task should finish with a concise report.

Use:

```text
## Final Change Report

### What changed
- ...

### Why
- ...

### Files changed
- `path/to/file`: reason

### Behavior impact
- ...

### Human readability
- PASS / PASS WITH NOTE / FAIL
- ...

### Human ownership
- Entry point: ...
- Main decision: ...
- Important invariant: ...

### Abstraction review
- Added abstractions: ...
- Justification: ...

### Verification
- Passed: ...
- Not run: ...
- Blocked: ...

### Risks / follow-up
- ...
```

Do not fabricate test results.

## Behavioral Rules for Codex

### Rule A — Do not over-engineer

When two implementations are correct, prefer the one with:

- fewer concepts,
- fewer files,
- fewer abstractions,
- fewer jumps,
- clearer control flow,
- easier debugging.

### Rule B — Do not hide business logic

Important business decisions should be easy to locate.

Avoid burying rules inside:

- generic utility functions,
- chains of callbacks,
- deeply nested abstractions,
- opaque framework wrappers.

### Rule C — Preserve local conventions

Before introducing a new pattern, inspect how the repository already solves similar problems.

Consistency is often more valuable than theoretical architectural purity.

### Rule D — Make AI-generated complexity visible

If the implementation becomes significantly more complex than the requested behavior, stop and simplify.

### Rule E — Explain unusual decisions

If code looks strange but is intentionally required, document the reason.

### Rule F — No fake certainty

Never say:

- "everything is verified"
- "no impact"
- "safe"
- "fully tested"

unless the evidence supports it.

## When to Use Full vs Lightweight Mode

### Lightweight mode

Use for:

- typo fixes,
- obvious one-line changes,
- formatting,
- simple constant changes,
- mechanical renames with no behavior change.

Still verify the change and avoid unnecessary comments.

### Full mode

Use for:

- new features,
- bug fixes involving behavior,
- refactoring,
- architecture changes,
- state management changes,
- API/network changes,
- persistence changes,
- device/platform integration,
- concurrency/asynchronous behavior,
- security-sensitive code,
- payment logic,
- code spanning multiple files.

## Completion Gate

Do not consider the task complete until all applicable gates pass:

```text
[ ] Understand
[ ] Plan
[ ] Implement
[ ] Verify
[ ] Human Readability Gate
[ ] Human Ownership Mode
[ ] Abstraction Control
[ ] Comment Enforcement
[ ] Change Impact Analysis
[ ] Final Change Report
```

The goal is not maximum documentation.

The goal is minimum complexity required for a human to safely understand and own the code.
