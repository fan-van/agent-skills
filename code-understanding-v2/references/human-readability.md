# Human Readability Gate

## Objective

Determine whether a human developer can understand the changed code without relying on the AI conversation.

## PASS signals

- main intent is obvious;
- important decisions are visible;
- names carry domain meaning;
- control flow is understandable;
- dependencies are reasonable;
- reader does not need to chase excessive indirection.

## FAIL signals

- simple behavior requires many layers;
- important logic is hidden in generic helpers;
- naming is technically correct but semantically vague;
- one function mixes unrelated responsibilities;
- comments are required to explain confusing control flow;
- understanding requires reconstructing AI reasoning.

## Simplification tactics

Prefer direct calls, explicit branching, domain-specific names, local transformations, fewer wrappers, and smaller coherent functions.

Do not optimize for fewer lines. Optimize for human comprehension.

## Reviewer question

"If I opened this file six months from now, could I understand the behavior without asking the original author?"
