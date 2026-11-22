# Flinkboot Testing

Follow these rules when writing or reviewing tests in a Flinkboot application using `flinkboot-test`.

## POJO Compliance Tests

- Add a unit test verifying `FlinkbootAssertions.assertThat(Model.class).isPojo()` for every Flink POJO, stream event model, and state value class.
- Use `FlinkbootAssertions.assertThat(new TypeHint<...>() {}).isPojo()` or `FlinkbootAssertions.assertThat(typeInfo).isPojo()` whenever verifying generic or composite Flink types whose type parameters would be erased by a `Class` literal.

## Operator and Function Serializability Tests

- Add a unit test verifying `FlinkbootAssertions.assertThat(instance).isSerializable()` for every custom Flink operator, user-defined function, and key selector.
- Instantiate the operator or function with realistic configuration arguments so accidental non-serializable fields or outer-class references fail locally before cluster submission.

## CollectingSink Usage in Pipeline Tests

- Wrap `CollectingSink` in a `try-with-resources` block so `close()` automatically clears its static in-memory registry after execution.
- Assert collected elements with `FlinkbootAssertions.assertThat(sink)`.
- Keep Flink object reuse disabled in tests that inspect collected elements so later records do not mutate previously collected references.
