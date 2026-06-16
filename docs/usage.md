# Usage

This repository is a source of truth for AI agent instructions and review presets.

All durable documentation copied from this repository should remain in English. Agents should act with Staff Engineer judgment, considering scale, operational risk, long-term maintenance, and system sustainability.

Agents should read `docs/project-overview.md` when present. If it is missing, they should inspect the project and suggest creating one before or alongside meaningful implementation work.

After code changes or implementation, agents should run applicable tests or validation checks and perform a brief security and reliability assessment. For frontend changes, agents should include browser-based validation when user flows, routing, forms, visual layout, responsiveness, authentication, checkout, onboarding, or other UI behavior is affected. If the project uses Playwright, Cypress, or another end-to-end framework, agents should run related tests for affected flows when practical.

For feature work, bug fixes, refactors, and behavior changes, agents should use test-driven development by default when automated tests are practical. Documentation-only changes, configuration-only changes, throwaway prototypes, generated code, or work where automated tests are not practical should explain the exception and use the smallest reliable reproduction available.

Agents should use DDD only when it clarifies meaningful business rules, domain boundaries, or invariants in a project that already uses or explicitly asks for that style. Agents should use SOLID to evaluate changed code without justifying broad refactors or new architecture, and use DRY to protect shared business rules without extracting similar-looking code prematurely.

Agents should calibrate rigor to risk: documentation-only changes need lightweight validation, behavior changes need TDD where practical and post-change assessment, and high-risk flows need security, reliability, rollout, rollback, and observability review.

## New Project Setup

1. Copy `templates/new-project-CLAUDE.md` into the target repository as `CLAUDE.md`.
2. Configure or prompt AI tools that do not discover `CLAUDE.md` automatically to read it before working.
3. Copy `templates/project-overview.md` to `docs/project-overview.md` if the target repository does not already have a project overview.
4. Copy or paste relevant presets from `presets/` into PR reviews, issue templates, or team documentation.

For existing or legacy repositories, prefer the README's agent-driven adoption prompt. It instructs the agent to inspect the target repository first, preserve project-specific guidance, merge duplicate content conservatively, and avoid blind overwrites.

## New Feature Planning

1. Use `templates/new-feature-request.md` to describe the feature request.
2. Use `presets/new-feature-planning.md` to generate a Staff Engineer-level plan.
3. Use `presets/ambiguity-resolution.md` when the plan has meaningful ambiguity or needs deliberate stress-testing.
4. Review scope, trade-offs, security, reliability, observability, test coverage, rollout, and rollback before implementation starts.
5. Use `presets/test-driven-implementation.md` for behavior-changing implementation work where automated tests are practical.
6. Use `presets/implementation-guidelines.md` when the feature is ready to build.

## Choosing Presets

- Use `engineering-review.md` for broad staff-level review.
- Use `change-risk-calibration.md` when the right validation depth is unclear.
- Use `new-feature-planning.md` before implementing a non-trivial feature.
- Use `ambiguity-resolution.md` when ambiguity is meaningful, the user asks for deliberate clarification, or a plan needs one-question-at-a-time stress-testing.
- Use `legacy-change-guidelines.md` when working in legacy or under-tested projects.
- Use `post-change-assessment.md` after code changes, behavior changes, or meaningful configuration changes.
- Use `test-driven-implementation.md` when implementing features, bug fixes, refactors, or behavior changes where automated tests are practical.
- Use `security-review.md` for auth, input, data exposure, uploads, dependencies, or webhook risks.
- Use `reliability-review.md` for async, queue, webhook, retry, timeout, and production failure risks.
- Use `test-review.md` before approval when test coverage is uncertain.
- Use `feature-flow-mapping.md` when onboarding to a feature or debugging an end-to-end path.
- Use `event-driven-flow-mapping.md` for queue, event, pub/sub, webhook, or async systems.

## Choosing Examples

- Use `examples/backend-service.md` for backend APIs and services.
- Use `examples/frontend-app.md` for frontend applications.

## Project Overview And Decisions

Read `docs/project-overview.md` to understand the current repository shape and operating model.

Use `templates/project-overview.md` to create a new onboarding-first project overview when a target repository does not already have one.

For meaningful development decisions, create one file under `docs/decisions/` using `templates/decision-log-entry.md`. Update `docs/project-overview.md` when the project purpose, structure, workflow, security model, or maintenance model changes.
