# TypeScript Type Safety

Follow these rules when designing types, interfaces, and runtime boundaries in TypeScript.

## Ban Unsafe Types and Casts

- Never use `any`; use `unknown` and narrow explicitly via type guards or runtime validation.
- Avoid type assertions (`as Type`, double casts `as unknown as Type`) and non-null assertions (`!`) unless an invariant is proven immediately above and impossible to express in the type system.
- Avoid `@ts-ignore` and `@ts-expect-error` in production code.

## Boundary Validation

- Never trust external data (HTTP responses, JSON payloads, CLI inputs, environment variables, filesystem reads) via static casts.
- Parse and validate all external inputs at system boundaries using the project's schema validator or explicit type guards before passing them into domain code.

## Data Modeling and Immutability

- Prefer discriminated unions and `as const` union types over TypeScript `enum` declarations.
- Enforce exhaustiveness checks (assigning the unhandled branch to `never`) when branching over discriminated unions so adding a variant fails at compile time.
- Prefer `readonly` properties, `ReadonlyArray<T>`, and `ReadonlyMap<K, V>` for data structures that should not be mutated by callers.
- Explicitly distinguish `undefined` (absent/optional) from `null` (intentional empty value) and keep conventions consistent across a module.
