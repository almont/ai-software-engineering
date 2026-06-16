# 0016: Consolidate Engineering Principles

## Status

Accepted

## Date

2026-06-16

## Context

The repository already guided agents toward clarity, tests, low coupling, DDD restraint, TDD where practical, and legacy architecture protection. The guidance needed a clearer combined treatment of DDD, TDD, SOLID, and DRY so agents apply these principles without turning them into excuses for broad refactors, premature abstractions, or architecture churn.

## Decision

Consolidate engineering-principle guidance across canonical instructions, templates, and implementation presets.

DDD is allowed only when it clarifies meaningful business rules, domain boundaries, or invariants in a project that already uses or explicitly asks for that style. Agents must not introduce DDD layers, terminology, or architecture migration work in projects that do not already use DDD unless the user explicitly requests it.

TDD remains the default for feature work, bug fixes, refactors, and behavior changes when automated tests are practical. When automated tests are not practical, agents should explain the exception and use the smallest reliable reproduction available.

SOLID should evaluate code already being changed, not justify broad refactors or new architecture. DRY should protect shared business rules and invariants from drift, not extract similar-looking code prematurely.

## Consequences

The guidance becomes more precise and harder to interpret as permission for opportunistic refactoring.

The trade-off is that agents have more text to read, but the added specificity should reduce overengineering and preserve existing project architecture.

## Follow-Up

Keep review presets aligned with this principle set when future review guidance changes.
