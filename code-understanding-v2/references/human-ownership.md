# Human Ownership Mode

The code must remain maintainable after the AI conversation disappears.

A human owner must be able to locate:

1. entry point;
2. main behavior;
3. important business rule;
4. side effects;
5. state changes;
6. invariants;
7. verification requirements.

## Ownership test

Ask:

- Where would I change this requirement?
- Where would I debug this behavior?
- What could break if I change this?
- Which test proves the behavior?
- Which external system is affected?

If the answers require extensive archaeology, reduce indirection or add targeted documentation.

Ownership is not documentation volume. Prefer code whose structure naturally communicates behavior.
