# Usage

This repository is a source of truth for AI agent instructions and review presets.

All durable documentation copied from this repository should remain in English. Agents should act with Staff Engineer judgment, considering scale, operational risk, long-term maintenance, and system sustainability.

## New Project Setup

1. Copy `templates/new-project-AGENTS.md` into the target repository as `AGENTS.md`.
2. Copy `templates/new-project-CLAUDE.md` into the target repository as `CLAUDE.md` if Claude will work on the project.
3. Copy `templates/new-project-copilot-instructions.md` into the target repository as `.github/copilot-instructions.md` if GitHub Copilot will be used.
4. Copy a permission guide from `permissions/` if the team wants documented safe actions.
5. Copy or paste relevant presets from `presets/` into PR reviews, issue templates, or team documentation.

## New Feature Planning

1. Use `templates/new-feature-request.md` to describe the feature request.
2. Use `presets/new-feature-planning.md` to generate a Staff Engineer-level plan.
3. Review scope, trade-offs, security, reliability, observability, test coverage, rollout, and rollback before implementation starts.
4. Use `presets/implementation-guidelines.md` when the feature is ready to build.

## Choosing Presets

- Use `engineering-review.md` for broad staff-level review.
- Use `new-feature-planning.md` before implementing a non-trivial feature.
- Use `security-review.md` for auth, input, data exposure, uploads, dependencies, or webhook risks.
- Use `reliability-review.md` for async, queue, webhook, retry, timeout, and production failure risks.
- Use `test-review.md` before approval when test coverage is uncertain.
- Use `feature-flow-mapping.md` when onboarding to a feature or debugging an end-to-end path.
- Use `event-driven-flow-mapping.md` for queue, event, pub/sub, webhook, or async systems.

## Permission Guides

The permission files document common safe local development actions. They are not permission engines by themselves. Use them as policy text when configuring Codex, Claude, or team workflows.
