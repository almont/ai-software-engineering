# 0002: Add Goal-Driven Surgical Agent Guidelines

## Status

Accepted

## Date

2026-05-25

## Context

The repository standardizes AI agent behavior across implementation, review, and project setup workflows. Existing instructions already emphasize Staff Engineer judgment, scope control, testing, security, reliability, and trade-off analysis.

The guidance needed a clearer standard for how agents should behave before and during implementation: state assumptions, surface ambiguity, prefer simple solutions, avoid speculative abstractions, keep changes surgical, and define verifiable success criteria.

## Decision

Add explicit goal-driven and surgical execution guidance to the canonical agent instructions and mirrored tool-specific instructions.

The guidance requires agents to:

- Think before coding by stating assumptions and asking when requirements are unclear.
- Present multiple reasonable interpretations instead of choosing silently.
- Prefer the minimum implementation that solves the stated problem.
- Avoid speculative features, flexibility, configurability, and single-use abstractions.
- Touch only files and lines required by the request.
- Remove only unused code created by their own changes.
- Convert multi-step tasks into verifiable goals with checks.

## Consequences

This makes agent behavior more predictable and reviewable, especially for implementation tasks where ambiguity or overengineering can create avoidable churn.

The trade-off is slightly longer instruction files and some intentional repetition across copy-ready templates. The repetition keeps the templates useful when copied into new repositories without depending on this repository as a live source.

## Follow-Up

Future presets and templates should preserve these principles when new agent workflows are added.
