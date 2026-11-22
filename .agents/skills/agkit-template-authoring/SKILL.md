---
name: agkit-template-authoring
description: "Authoring and validating modules in an AGKIT template repository. Use when creating, structuring, or validating modules under modules/."
---

# AGKIT Template Authoring

Before creating, modifying, or validating modules, skills, or agents in this repository, always run `agkit spec` and treat its output as the single source of truth for directory layout, JSON schemas, and validation invariants.

## Core Rules

- Place every module under `modules/<module-id>/` with a valid `module.json` (`display_name`, `description`).
- Use lowercase `kebab-case` names for all module, skill, and agent directories.
- Keep modules independent and composable: there is no implicit `base` module and no module inheritance.
- Keep `ROOT.md`, `SKILL.md`, and `PROMPT.md` as pure Markdown without manual YAML frontmatter; `agkit` generates harness-specific frontmatter automatically.
- Give skills and agents unique IDs across modules that users may combine together (duplicate IDs fail fast during composition).

## Specialized Guides

- Use `agkit-root-authoring` when writing `ROOT.md`.
- Use `agkit-skill-authoring` when writing `skills/<skill-id>/`.
- Use `agkit-agent-authoring` when writing `agents/<agent-id>/`.
