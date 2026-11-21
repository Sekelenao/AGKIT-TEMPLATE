## Java Guidelines

- Prefer immutable data carriers (`record`, `final` fields, unmodifiable collections).
- Avoid `null` returns for absent values; prefer `Optional` on public APIs.
- Close I/O resources with `try-with-resources`.
