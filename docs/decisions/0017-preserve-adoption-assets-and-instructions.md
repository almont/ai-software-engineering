# Preserve Adoption Assets And Instructions

## Status

Accepted

## Date

2026-06-16

## Context

The agent-driven adoption workflow previously told agents to copy or adapt relevant presets and templates. In legacy projects, that language can lead an agent to copy only the files it judges necessary for the immediate task.

The same risk applies to instruction files. Existing `CLAUDE.md`, legacy `AGENTS.md`, Copilot instructions, Cursor rules, and similar files may contain operational knowledge that is not obviously relevant during setup but is needed later.

## Decision

Treat `presets/` and `templates/` as operational assets that must be copied completely and recursively during adoption.

Treat `CLAUDE.md` as the canonical destination for agent instructions. Existing instruction files may be merged into `CLAUDE.md`, but the merge must preserve all operational instructions, conventions, commands, architecture notes, testing guidance, restrictions, and warnings. Merging must not become selective copying, summarizing, or filtering based on perceived relevance.

If instructions conflict, preserve the conflict and mark it for human review.

Keep this rule in the adoption prompt and supporting usage documentation. Do not add it to the canonical `CLAUDE.md` or `templates/new-project-CLAUDE.md`, because those files describe how agents should work inside an already adopted project.

## Consequences

Adoption is less likely to lose files or legacy operating knowledge that becomes important later.

The trade-off is that target repositories may receive more files than they immediately use. That is acceptable because these assets are intentionally reusable and can be reviewed after adoption.

## Follow-Up

Keep README adoption guidance, usage docs, and project overview aligned on this rule.
