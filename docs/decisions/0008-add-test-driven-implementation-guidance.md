# Add Test-Driven Implementation Guidance

## Status

Accepted

## Date

2026-06-15

## Context

The repository already requires automated tests and post-change validation, but it did not make test-first implementation the default. That left room for agents to implement behavior first and add tests afterward, which weakens confidence that tests capture the intended behavior.

The team wants agents to act with TDD discipline where it is useful without making documentation-only or test-impractical work unnecessarily bureaucratic.

## Decision

Make test-driven development the default for feature work, bug fixes, refactors, and behavior changes when automated tests are practical.

Agents should write or identify the smallest failing test or reproduction first, confirm it fails for the expected reason, implement the smallest passing change, then refactor while tests remain green.

Add `presets/test-driven-implementation.md` as the reusable workflow for this behavior. Allow explicit exceptions for documentation-only changes, configuration-only changes, throwaway prototypes, generated code, and work where automated tests are not practical, provided the agent explains the exception and uses the closest validation available.

## Consequences

This improves behavioral confidence, regression protection, and reviewability.

The trade-off is that some implementation tasks will take longer up front. That cost is intentional for behavior-changing work, while exception handling keeps low-risk documentation and configuration work lightweight.

## Follow-Up

Watch whether teams need project-specific guidance for applying TDD in UI, integration-heavy, or legacy projects with weak test infrastructure.
