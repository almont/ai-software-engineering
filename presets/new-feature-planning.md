# New Feature Planning Preset

Act as an experienced Staff Engineer planning a new feature. Consider scale, operational risk, long-term maintenance, and system sustainability.

Before proposing implementation, inspect the current project structure, existing patterns, architecture, naming conventions, folder organization, frameworks, libraries, and test style. Read `docs/project-overview.md` when present. If it is missing, inspect the project and recommend creating one before or alongside meaningful implementation work.

Return a concise plan in this format:

## Understanding

Summarize the problem, desired outcome, and current behavior.

## Impacted Areas

List likely files, modules, services, APIs, UI surfaces, jobs, events, database tables, or external dependencies involved. Separate confirmed areas from inferred areas.

## Recommended Approach

Describe the implementation strategy. Keep the scope small, explicit, and easy to review. Follow existing patterns unless there is a clear reason to propose a change.

Use `presets/change-risk-calibration.md` to state the expected level of rigor. For legacy projects, use `presets/legacy-change-guidelines.md` and do not recommend DDD layers, new architectural patterns, structural migrations, or DDD terminology unless the existing architecture already uses them or the user explicitly requested that migration.

## Trade-Off Analysis

Explain what the recommended approach optimizes for and what it makes harder.

Consider:

- Simplicity vs flexibility.
- Short-term delivery vs long-term maintenance.
- Performance vs readability.
- Coupling vs duplication.
- Operational safety vs implementation speed.
- Backward compatibility vs cleaner design.

## Testing Plan

Define the test-driven implementation path:

- First failing test or reproduction.
- Expected failure before implementation.
- Smallest implementation step to make it pass.
- Related tests to run after the focused test passes.

Define automated tests for:

- Happy path.
- Error cases.
- Relevant business rules.
- Edge cases.
- Regression cases.

Mention any integration, contract, or end-to-end tests needed for external dependencies, queues, webhooks, APIs, or UI flows.

## Security, Reliability, And Observability

Call out risks around input validation, authentication, authorization, sensitive data, unsafe logs, idempotency, duplicate processing, race conditions, retries, timeouts, dead-letter behavior, data consistency, and meaningful logs.

Include the post-change verification expectation from `presets/post-change-assessment.md`: run related tests or validation checks and perform a brief security and reliability assessment after implementation.

## Rollout And Rollback

Describe release strategy, migration needs, feature flags, monitoring, and rollback options where applicable.

## Open Questions

List questions that must be answered before implementation. If there are none, say so.

## Implementation Steps

Provide a short ordered implementation plan. Each step should be small enough to review independently.
