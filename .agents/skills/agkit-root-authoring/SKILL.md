---
name: agkit-root-authoring
description: "Authoring ROOT.md project-wide instructions inside AGKIT template modules. Use when creating or updating a module ROOT.md file."
---

# AGKIT Root Instructions Authoring

Run `agkit spec` first to verify repository layout and composition rules.

## Rules

- Design for concatenation: `agkit` concatenates `ROOT.md` from all selected modules in selection order. Use self-contained `##` sections and do not assume this module is the only or first `ROOT.md` in the output.
- Stay harness-agnostic: `agkit` renders `ROOT.md` to `AGENTS.md` or `CLAUDE.md` depending on the target harness. Do not hardcode harness-specific filenames (`AGENTS.md`, `CLAUDE.md`) or tool directories (`.claude/`, `.opencode/`, `.agents/`, `.bob/`).
- Pure Markdown only: do not add manual YAML frontmatter to `ROOT.md`.
- Keep instructions high-signal and concise: include only always-relevant project invariants and pointers in `ROOT.md`. Move detailed workflows, checklists, and domain standards into dedicated skills under `skills/<skill-id>/`.
- Avoid cross-module contradictions: scope rules clearly to the module domain so combining multiple modules does not produce conflicting guidance.
