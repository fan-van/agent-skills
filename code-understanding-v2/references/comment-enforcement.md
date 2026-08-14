# Comment Enforcement

Comments preserve knowledge that cannot be safely inferred from code.

## Good comment targets

- external limitations;
- platform quirks;
- compatibility workarounds;
- business rules;
- safety constraints;
- non-obvious ordering;
- timing requirements;
- invariants.

## Avoid

- line-by-line narration;
- obvious comments;
- stale explanations;
- comments that merely repeat names;
- giant comments explaining code that should instead be simplified.

## Rule

Explain WHY, not WHAT.

A durable comment should remain true when variable names or implementation details change.
