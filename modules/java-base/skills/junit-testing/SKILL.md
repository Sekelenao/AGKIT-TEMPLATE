---
name: junit-testing
description: Standards for writing fast, deterministic JUnit 5 tests. Use when creating or updating Java unit tests.
---

# JUnit 5 Testing

- Prefer deterministic unit tests over heavy Spring/container contexts when testing pure domain logic.
- Use `@ParameterizedTest` to consolidate repetitive cases sharing the same invariant.
- Avoid mocking value objects or the class under test.
