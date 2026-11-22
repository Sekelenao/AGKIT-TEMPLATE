## Flinkboot

This project uses Flinkboot, a bootstrapping and reliability framework for Apache Flink.
Flinkboot handles fail-fast YAML configuration loading and validation, declarative `StreamExecutionEnvironment` setup, connector factories, and zero-Kryo POJO and serializability test assertions.
Prefer Flinkboot APIs and conventions over manual Flink boilerplate whenever available.
For up-to-date API reference and documentation, consult `https://flinkboot.com/llms.txt`.
