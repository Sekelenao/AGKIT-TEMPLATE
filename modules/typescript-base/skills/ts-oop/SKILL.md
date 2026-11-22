# TypeScript Object-Oriented Design

Follow these principles when structuring TypeScript code with object-oriented design.

## Encapsulation and State Ownership

- Model domain concepts and stateful collaborators as classes that co-locate data with the behavior operating on it, rather than scattering loose procedural helpers over mutable plain objects.
- Declare explicit member visibility (`private`, `protected`, `public`) on class properties and methods; keep internal state `private` and `readonly` by default.
- Enforce class invariants at construction time (or via dedicated static factory methods when validation is asynchronous or fallible) so instances are never left in an invalid state.
- Avoid exposing public setters that allow arbitrary external mutation; expose intention-revealing domain methods instead.

## Interfaces, Composition, and Dependency Injection

- Favor composition over inheritance; use class inheritance only when a genuine behavioral subtype relationship exists and avoid deep inheritance hierarchies.
- Inject external collaborators and side-effecting dependencies through constructors rather than importing and calling module-level singletons directly.
- Define TypeScript `interface` contracts at architectural boundaries or where genuine polymorphism is needed; do not create redundant one-to-one interfaces for internal classes with a single implementation.

## Clean Class Boundaries

- Keep each class focused on a single cohesive responsibility and axis of change.
- Prefer pure, small methods over large multi-purpose methods, and avoid static utility bags when behavior belongs on a domain object.
