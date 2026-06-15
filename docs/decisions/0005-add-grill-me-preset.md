# Add Grill Me Ambiguity Preset

## Status

Accepted

## Date

2026-06-15

## Context

The repository already instructs agents to surface ambiguity and ask when requirements are unclear. The team wanted a reusable workflow for cases where a plan or design needs more deliberate clarification before implementation.

The requested behavior was inspired by a skill that interviews the user relentlessly, explores the codebase for answers when possible, and recommends an answer for each question.

## Decision

Add `presets/grill-me.md` as an optional ambiguity-resolution preset. The preset is recommended when the user asks to be grilled, when a plan needs stress-testing, or when meaningful ambiguity should be resolved before implementation.

Reference the preset from the canonical agent instructions, project templates, usage documentation, README, and project overview.

## Consequences

This keeps the repository documentation-first and avoids turning every task into a mandatory interview. Agents get a clear workflow for resolving ambiguity while preserving fast paths for straightforward, low-risk work.

The trade-off is that adoption depends on agents and users recognizing when the optional preset should be used.

## Follow-Up

Watch whether the preset is too verbose in practice. If teams use it frequently, consider adding a shorter variant for small decisions.
