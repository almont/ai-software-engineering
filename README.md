# AI Presets Boilerplate

Reusable AI agent presets for Codex, Claude, GitHub Copilot, and team review workflows.

This repository is intentionally documentation-first. It is a source of truth for agent behavior, review prompts, and safe development permission guidance that can be copied into new projects. There is no install script, package manager, or runtime.

## Purpose

Use this repository to standardize how AI agents work across projects:

- How agents should implement features and fixes.
- How agents should review code.
- How agents should reason about security, reliability, tests, and trade-offs.
- Which local development actions are commonly safe.
- Which actions require explicit approval.

The goal is not to create a complex framework. The goal is to make agent behavior consistent, reviewable, and easy to reuse.

## Agent Behavior

Agents using these presets should act as experienced Staff Engineers. They should consider:

- Clarity.
- Automated tests.
- Low coupling.
- Maintainability.
- Scale.
- Operational safety.
- Backward compatibility.
- System sustainability.
- Trade-off analysis.

For non-trivial changes, agents should explain what the chosen approach optimizes for and what it makes harder. They should prefer small, explicit, easy-to-review changes over broad rewrites.

All durable repository documentation should be written in English.

## Repository Structure

```text
/
  README.md
  AGENTS.md
  CLAUDE.md
  .github/
    copilot-instructions.md
  presets/
  permissions/
  templates/
  examples/
  docs/
```

## Core Files

- `AGENTS.md`: canonical Codex instructions for new repositories.
- `CLAUDE.md`: Claude-compatible project instructions.
- `.github/copilot-instructions.md`: GitHub Copilot custom instructions.
- `presets/`: reusable review, implementation, and flow-mapping prompts.
- `permissions/`: common safe development allowlists for Codex and Claude.
- `templates/`: copy-ready files and review requests.
- `examples/`: project-specific preset combinations.
- `docs/`: usage and maintenance guidance.

## How To Use In A New Project

1. Copy `templates/new-project-AGENTS.md` to `AGENTS.md` in a target repository.
2. Copy `templates/new-project-CLAUDE.md` to `CLAUDE.md` if the project uses Claude.
3. Copy `templates/new-project-copilot-instructions.md` to `.github/copilot-instructions.md` if the project uses GitHub Copilot.
4. Copy the relevant files from `presets/` into the target repo or paste them into review requests.
5. Copy the relevant file from `permissions/` if you want a documented allowlist.

## Available Presets

- `presets/engineering-review.md`: staff-level review focused on business impact, architecture, security, reliability, observability, tests, and operational risk.
- `presets/security-review.md`: security review for injection, auth, authorization, sensitive data, SSRF, unsafe upload, webhook spoofing, validation, and rate limits.
- `presets/reliability-review.md`: reliability review for retries, timeouts, idempotency, race conditions, dead-letter queues, partial failures, observability, rollback, and data consistency.
- `presets/test-review.md`: test coverage review for unit, integration, contract, happy path, error path, edge case, and regression coverage.
- `presets/implementation-guidelines.md`: implementation workflow for feature work and bug fixes.
- `presets/feature-flow-mapping.md`: end-to-end feature flow mapping.
- `presets/event-driven-flow-mapping.md`: producer, consumer, payload, retry, ordering, DLQ, and idempotency mapping.

## Permission Guides

The permission guides define common local development actions that are usually safe:

- Read, list, and search files.
- Inspect git status, diffs, branches, and logs.
- Run tests, lint, format, typecheck, builds, and local dev servers.
- Use `npm`, `pnpm`, and `yarn` for project scripts.
- Use `gh` for non-destructive GitHub workflows.
- Use `docker` and `docker compose` for local development.

They also define actions that require explicit approval:

- Destructive file or git operations.
- Pushing, merging, tagging, releasing, or deploying.
- Production data access or mutation.
- Secret, token, key, or credential handling.
- Authentication, authorization, permission, infrastructure, or CI/CD changes.
- Payment, billing, webhook, or money-movement behavior changes.
- Database migrations, schema deletion, or data deletion.
- Docker prune or delete operations.
- Unknown tool installs or untrusted network commands.

## Example Starting Points

- Use `examples/backend-service.md` for backend APIs and services.
- Use `examples/frontend-app.md` for frontend applications.
- Use `examples/billing-payments.md` for payment, billing, webhook, or money-movement systems.

## Maintenance Rules

Treat `AGENTS.md` as the canonical source. When standards change:

1. Update `AGENTS.md`.
2. Mirror relevant guidance into `CLAUDE.md`.
3. Condense relevant guidance into `.github/copilot-instructions.md`.
4. Update matching files in `templates/`.
5. Update `presets/`, `permissions/`, and `examples/` if needed.
6. Review `docs/usage.md` and `docs/maintenance.md`.

Keep documentation in English, even when the original request or conversation is in another language.

## Design Choice

This repository does not include an apply script yet. Manual copying keeps the first version transparent and easy to audit. If repeated setup becomes painful, an optional script can be added later without changing the documentation model.
