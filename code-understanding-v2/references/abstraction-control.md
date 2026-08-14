# Abstraction Control

Prevent AI-generated architecture from becoming more complicated than the problem.

For every meaningful new abstraction, identify:

- concrete current problem;
- current duplication or boundary;
- why existing code is insufficient;
- cognitive cost;
- repository precedent if any.

These are not sufficient by themselves:

- future scalability;
- flexibility;
- SOLID compliance;
- "clean architecture";
- theoretical reuse.

If one business operation becomes Controller → Manager → Service → Provider → Repository → Adapter → Helper, inspect whether every layer is necessary.

Use the least abstraction that preserves correctness, testability, and maintainability.
