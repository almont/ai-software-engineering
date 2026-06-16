# Unify Agent Instructions In CLAUDE.md

## Status

Accepted

## Date

2026-06-15

## Context

The repository previously maintained separate instruction files for Codex, Claude, and GitHub Copilot. That improved tool-specific discovery, but it also created repeated guidance and ongoing drift risk.

The team wants one source of truth for agent behavior while still allowing non-Claude tools to use the same documentation when explicitly configured or prompted to read it.

## Decision

Use `CLAUDE.md` as the single canonical AI agent instruction file.

Remove tool-specific instruction files and templates:

- `AGENTS.md`
- `.github/copilot-instructions.md`
- `templates/new-project-AGENTS.md`
- `templates/new-project-copilot-instructions.md`

Update README, usage, maintenance, overview, examples, and the local import workflow to direct all agents to `CLAUDE.md`.

## Consequences

This reduces duplication and drift across agent instruction files.

The trade-off is weaker automatic discovery for tools that expect `AGENTS.md` or `.github/copilot-instructions.md`. Those tools must be configured or prompted to read `CLAUDE.md` explicitly.

## Follow-Up

If a future workflow requires automatic discovery for a specific tool, prefer a tiny adapter only if the team accepts reintroducing tool-specific files.
