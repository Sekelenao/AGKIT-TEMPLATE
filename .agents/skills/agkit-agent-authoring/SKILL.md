---
name: agkit-agent-authoring
description: "Authoring specialized agents (agent.json and PROMPT.md) inside AGKIT template modules. Use when creating, updating, or reviewing an agent under modules/<module>/agents/."
---

# AGKIT Agent Authoring

Run `agkit spec` first to verify the `agent.json` schema and allowed `capabilities` values.

## Rules

- Directory and naming: place each agent in `modules/<module-id>/agents/<agent-id>/` with lowercase `kebab-case` `<agent-id>`, `agent.json`, and `PROMPT.md`. Give each agent a focused, well-bounded mission and ensure `<agent-id>` does not collide with agents in other modules users may combine.
- Metadata in `agent.json`: set a clear `display_name`, a concise `description`, and an action-oriented `when_to_use` stating when the harness should invoke or suggest the agent—and when it should not be used.
- Least-privilege `capabilities`: explicitly list only the capabilities the agent needs from `read`, `edit`, `execute`, `skill`, and `subagent`. Omitting `capabilities` grants all capabilities.
- Optional `mode` and `skills`: set `mode` (`"subagent"`, `"primary"`, or `"all"`) when controlling primary vs subagent availability, and list lowercase `kebab-case` skill IDs under `skills` when declaring explicit skill dependencies for harnesses that support them.
- Optional `file_regex`: set `file_regex` only when the agent must be restricted to specific file paths (used by harnesses that support file scoping such as IBM Bob).
- Pure Markdown in `PROMPT.md`: do not add manual YAML frontmatter; `agkit` translates `agent.json` and `PROMPT.md` into each harness's native format.
- Structured, harness-agnostic `PROMPT.md`: organize the prompt around Mission, Inputs and Context, ordered Workflow, Constraints and Boundaries, and Output Format. Do not hardcode harness-specific paths, vendor-only syntax, or metadata field names inside `PROMPT.md`.
- Role over duplicated rules: delegate detailed coding or domain standards to reusable skills rather than duplicating them. Avoid illustrative examples in `PROMPT.md` that narrow or anchor the agent's judgment toward specific cases; use minimal structural templates only when output format ambiguity is costly. Avoid decorative Markdown emphasis (bold/italic asterisks) to save tokens.
