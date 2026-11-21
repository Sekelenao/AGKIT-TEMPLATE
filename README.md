# AGKIT Template Repository

Central repository of composable, harness-agnostic AI templates consumed by `agkit`.

## Structure

Each module lives under `modules/<module-id>/` (lowercase `kebab-case`) and must contain a `module.json` manifest:

```text
modules/
├── base/
│   ├── module.json
│   ├── ROOT.md
│   ├── skills/
│   │   └── git-conventions/
│   │       ├── SKILL.md
│   │       └── references/
│   │           └── commit-examples.md
│   └── agents/
│       └── code-reviewer.md
├── java-base/     # extends: ["base"]
└── flink/         # extends: ["java-base"]
```

## Available Modules

| Module ID | Display Name | Extends | Description |
| --- | --- | --- | --- |
| `base` | Base | — | Shared engineering guidelines, Git conventions, and code reviewer agent |
| `java-base` | Java Base | `base` | Shared Java conventions and JUnit testing skill |
| `flink` | Apache Flink | `java-base` | Apache Flink streaming rules and operator checklist |
