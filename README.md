# AGKIT Templates

Personal repository of composable, harness-agnostic AI instructions, skills, and specialized agents managed with [`agkit`](https://github.com/Sekelenao).

## Available Modules

| Module | Contents | Purpose |
| --- | --- | --- |
| `ai-authoring` | Skills: `skill-authoring`, `agent-authoring` | Harness-agnostic principles for writing concise, non-narrowing AI skills and agents |
| `engineering` | `ROOT.md`, Skills: `oop-software-design`, `git-commits` | Stack-agnostic software engineering standards for OOP design, Conventional Commits, and clean workflows |
| `java-base` | Skills: `java-nullability`, `java-classes-and-records`, `java-testing` | Core Java standards for null safety, immutability, records/classes, and JUnit 5 testing |
| `java-flink` | Skills: `flink-hot-path`, `flink-pojo` | Production Apache Flink Java practices for low-allocation hot paths and zero-Kryo POJOs |
| `java-flinkboot` | `ROOT.md`, Skills: `flinkboot-configuration`, `flinkboot-testing` | Declarative YAML configuration, fail-fast validation, and `flinkboot-test` assertions |
| `java-springboot` | `ROOT.md`, Skills: `springboot-configuration`, `springboot-properties` | Production Spring Boot practices for native conventions, clean bootstrap/configuration classes, and type-safe validated properties |
| `typescript-base` | Skills: `ts-type-safety`, `ts-classes`, `ts-error-handling`, `ts-testing` | Core TypeScript standards for strict typing, clean classes, typed errors, and testing |
| `agent-swarm` | Agents: `refiner`, `orchestrator`, `implementer`, `prod-auditor`, `test-auditor` | Stack-agnostic multi-agent workflow from refinement to parallel implementation and independent audits |

## Usage

Configure this repository once:

```bash
agkit config --repo https://github.com/Sekelenao/AGKIT-TEMPLATE.git
agkit list
```

Initialize any combination of modules in a target project:

```bash
# Java + Apache Flink + Flinkboot + Agent Swarm
agkit init -m java-base java-flink java-flinkboot agent-swarm --harness claude

# TypeScript + Agent Swarm
agkit init -m typescript-base agent-swarm --harness opencode

# Sync later with upstream updates
agkit sync
```

## Authoring

Run `agkit spec` to inspect the full repository layout, JSON schemas, and validation invariants before adding or updating modules under `modules/`.
