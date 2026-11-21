## Apache Flink Guidelines

- Assign explicit `.uid(...)` to every stateful operator to guarantee savepoint compatibility.
- Avoid blocking I/O inside synchronous `MapFunction` / `ProcessFunction` operators; use `AsyncDataStream` when calling external services.
- Configure bounded out-of-orderness watermarks and explicit idle-source timeouts on event-time pipelines.
