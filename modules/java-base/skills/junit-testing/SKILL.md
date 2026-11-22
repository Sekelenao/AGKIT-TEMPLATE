# JUnit 5 Testing

- Prefer deterministic unit tests over heavy Spring/container contexts when testing pure domain logic.
- Use `@ParameterizedTest` to consolidate repetitive cases sharing the same invariant.
- Avoid mocking value objects or the class under test.
