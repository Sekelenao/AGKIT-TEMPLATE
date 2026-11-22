---
name: agkit-skill-authoring
description: "Authoring reusable skills (skill.json and SKILL.md) inside AGKIT template modules. Use when creating, updating, or reviewing a skill under modules/<module>/skills/."
---

# AGKIT Skill Authoring

Run `agkit spec` first to verify the `skill.json` schema and directory conventions.

## Rules

- Directory and naming: place each skill in `modules/<module-id>/skills/<skill-id>/` with lowercase `kebab-case` `<skill-id>`, `skill.json`, and `SKILL.md`. Give each skill a single, cohesive responsibility and ensure `<skill-id>` and its trigger scope do not collide with skills in other modules users may combine.
- Trigger-oriented `skill.json`: write a concise `description` stating both what the skill covers and when the AI should activate it. Keep it portable across all supported harnesses.
- Pure Markdown in `SKILL.md`: do not add manual YAML frontmatter; `agkit` generates harness-native frontmatter automatically.
- Direct, general instructions: write imperative rules focused on invariants, decision criteria, and workflows instead of background prose or duplicated root conventions. Avoid putting examples in `SKILL.md` rules to prevent narrowing or anchoring the AI's behavior toward specific cases.
- Stay harness-agnostic: do not hardcode harness-specific paths (`.claude/skills/`, `.opencode/skills/`, `.agents/skills/`, `.bob/skills/`) or harness-specific metadata field names inside `SKILL.md`. Reference companion files with relative paths.
- Progressive disclosure: keep `SKILL.md` concise. Place lengthy reference docs, checklists, templates, or helper scripts in companion subdirectories (`references/`, `scripts/`), which `agkit` copies as-is.
