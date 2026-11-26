# AGKIT Templates

Personal repository of composable, harness-agnostic AI instructions, skills, and specialized agents managed with [`agkit`](https://github.com/Sekelenao).

## Available Modules

| Module | Contents | Purpose |
| --- | --- | --- |
| `ai-authoring` | Skills: `skill-authoring`, `agent-authoring` | Harness-agnostic principles for writing concise, non-narrowing AI skills and agents |
| `engineering` | `ROOT.md`, Skills: `oop-software-design`, `git-commits` | Stack-agnostic software engineering standards for OOP design, Conventional Commits, and clean workflows |
| `java-base` | Skills: `java-nullability`, `java-classes-and-records`, `java-testing`, `java-targeted-testing` | Core Java standards for null safety, immutability, records/classes, JUnit 5 testing, and targeted test execution |
| `java-flink` | Skills: `flink-hot-path`, `flink-pojo` | Production Apache Flink Java practices for low-allocation hot paths and zero-Kryo POJOs |
| `java-flinkboot` | `ROOT.md`, Skills: `flinkboot-configuration`, `flinkboot-testing` | Declarative YAML configuration, fail-fast validation, and `flinkboot-test` assertions |
| `java-springboot` | `ROOT.md`, Skills: `springboot-configuration`, `springboot-properties` | Production Spring Boot practices for native conventions, clean bootstrap/configuration classes, and type-safe validated properties |
| `typescript-base` | Skills: `ts-type-safety`, `ts-classes`, `ts-error-handling`, `ts-testing` | Core TypeScript standards for strict typing, clean classes, typed errors, and testing |
| `agent-audit` | Agents: `prod-auditor`, `test-auditor`, `code-scanner`, `pr-reviewer` | Stack-agnostic review and audit agents for production diffs, tests, full module scans, and PR reviews |
| `agent-swarm` | Agents: `refiner`, `orchestrator`, `implementer` | Stack-agnostic multi-agent workflow for multi-slice refinement and parallel implementation (pairs with `agent-audit`) |

## Usage

Configure this repository once:

```bash
agkit config --repo https://github.com/Sekelenao/AGKIT-TEMPLATE.git
agkit list
```

Initialize any combination of modules in a target project:

```bash
# Java + Apache Flink + Flinkboot + Audit agents (solo workflow with on-demand audits)
agkit init -m engineering java-base java-flink java-flinkboot agent-audit --harness claude

# TypeScript + Full Agent Swarm (multi-slice workflow + audits)
agkit init -m engineering typescript-base agent-swarm agent-audit --harness opencode

# Sync later with upstream updates
agkit sync
```

## Authoring

Run `agkit spec` to inspect the full repository layout, JSON schemas, and validation invariants before adding or updating modules under `modules/`.
