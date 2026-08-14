# Verification

Verify behavior using evidence, not confidence.

## Levels

1. Syntax / formatting
2. Static analysis / type checking
3. Targeted unit tests
4. Integration tests
5. Build / compile
6. Runtime behavior

Use only levels relevant to the repository and change.

## Reporting

Always distinguish:

- PASSED
- NOT RUN
- BLOCKED
- FAILED
- PRE-EXISTING FAILURE

Never convert "not run" into "passed".

If verification fails, determine whether the failure is caused by the change, fix it when in scope, otherwise report it explicitly.
