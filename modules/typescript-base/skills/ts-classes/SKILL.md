# TypeScript Classes

Follow these rules when designing and implementing TypeScript classes and interfaces.

## Visibility and Encapsulation

- Declare explicit member visibility (`private`, `public`) on class fields and methods; keep internal state `private` and `readonly` by default.
- Enforce invariants in the constructor (or a dedicated static factory method when validation is asynchronous or fallible) so instances are never left in an invalid state.
- Avoid public setters that allow arbitrary external mutation; expose intention-revealing methods instead.
- Model stateful domain concepts and collaborators as classes rather than scattering loose procedural helpers over mutable plain objects.

## Composition and Interfaces

- Never use class-to-class inheritance (`extends`) in application or domain code; use composition and TypeScript `interface` contracts instead (except when extending built-in `Error` for custom error classes or framework-mandated base classes).
- Inject external collaborators and side-effecting dependencies through constructors rather than importing and calling module-level singletons directly.
- Define TypeScript `interface` contracts at architectural boundaries or where genuine polymorphism is needed; do not create redundant one-to-one interfaces for internal classes with a single implementation.
