# 0015: Replace Import Script With Agent Adoption Prompt

## Status

Accepted

## Date

2026-06-16

## Context

The README previously included a shell snippet for copying presets into a target repository. That flow was conflict-safe, but it treated adoption mostly as file copying. For legacy projects, project-specific instructions, architecture notes, commands, docs, and team conventions can contain important context that should be preserved and merged intentionally.

Because this repository exists to guide AI agents, an agent-driven adoption prompt fits the project better than a copy script.

## Decision

Replace the README import script with an agent adoption prompt.

The prompt explicitly names the source presets repository, treats the current working directory as the target repository, requires target inspection before source adoption, and tells agents to preserve existing project knowledge before adding generic guidance.

The prompt also tells agents to merge conservatively, prefer target-specific guidance over source guidance, avoid blind overwrites, and ask before removing existing project-specific instructions.

## Consequences

Adoption becomes more suitable for legacy repositories and less likely to discard local context.

The trade-off is that adoption now depends on an AI agent with repository access instead of a deterministic shell copy operation.

## Follow-Up

Keep the adoption prompt aligned with project setup guidance, project overview expectations, and legacy-change guidance.
