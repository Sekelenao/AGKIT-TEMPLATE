# TypeScript Testing

Follow these rules when creating, updating, or reviewing TypeScript unit tests.

## Structure and Clarity

- Organize tests with clear `describe` blocks grouped by class, feature, or behavior, and concise `it` / `test` descriptions stating the expected outcome.
- Test the public API and observable behavior rather than private implementation details.
- Isolate test state cleanly using `beforeEach` / `afterEach` and reset or restore mocks after every test so tests never leak state across cases.

## Behavioral Focus and Anti-Tautologies

- Reject compiler and mock tautologies: never write tests that only verify TypeScript static types or assert that a mock returned the value stubbed into it without exercising real logic.
- Every test must fail if a realistic human mistake or production code mutation is introduced.
- Cover boundary conditions, `undefined` and `null` inputs, empty collections, error paths, and rejected promises.

## Parameterized Tests (Goldilocks Rule)

- Consolidate repetitive test cases verifying the same single invariant using parameterized tables (`it.each` / `test.each`).
- Never merge distinct business concepts, intentions, or outcomes into a single parameterized table merely to reduce line count; each distinct behavioral path deserves its own test.
- Never write parameterized tests containing conditional branching or heterogeneous assertions; a parameterized test must verify one invariant at a glance.

## Mutation and Invariant Sensitivity

- Write assertions that strictly fail if a production condition is inverted, swapped, or omitted.
- Avoid symmetry blindspots: test asymmetric combinations of flags or options, not only uniform combinations.
- Keep assertions on unordered structures deterministic: never depend on iteration order of `Set` or unordered keys; assert exact counts and match elements explicitly.
