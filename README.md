# AI Presets Boilerplate

Reusable AI agent instructions, presets, and team review workflows centered on one canonical `CLAUDE.md` file.

This repository is intentionally documentation-first. It is a source of truth for agent behavior, review prompts, and reusable project setup guidance that can be copied into new projects. There is no install script, package manager, or runtime.

## Purpose

Use this repository to standardize how AI agents work across projects:

- How agents should implement features and fixes.
- How agents should apply test-driven development where practical.
- How agents should plan new features before implementation.
- How agents should review code.
- How agents should reason about security, reliability, tests, and trade-offs.
- How agents should apply DDD, TDD, SOLID, and DRY without overengineering.
- How agents should orient themselves with project overview documentation before implementation.

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

Agents should use DDD only when it clarifies meaningful business rules, domain boundaries, or invariants in a project that already uses or explicitly asks for that style. In legacy projects, agents should not introduce DDD layers, new architectural patterns, structural migrations, or DDD terminology unless the existing architecture already uses them or the user explicitly requests that migration.

Agents should use SOLID to evaluate code they are already changing, not to justify broad refactors or new architecture. They should use DRY to protect shared business rules, invariants, calculations, validation, policies, and workflows from drifting, not to extract similar-looking code prematurely.

Agents should read `docs/project-overview.md` when present. If it is missing, they should inspect the project and suggest creating one before or alongside meaningful implementation work.

After code changes or implementation, agents should run applicable tests or validation checks and perform a brief security and reliability assessment. For frontend changes, agents should include browser-based validation when user flows, routing, forms, visual layout, responsiveness, authentication, checkout, onboarding, or other UI behavior is affected. If the project uses Playwright, Cypress, or another end-to-end framework, agents should run related tests for affected flows when practical.

For feature work, bug fixes, refactors, and behavior changes, agents should use test-driven development by default when automated tests are practical: write or identify a failing test or reproduction first, make the smallest passing change, then refactor while tests stay green. When automated tests are not practical, agents should explain why TDD does not apply and use the smallest reliable reproduction available.

Agents should calibrate rigor to risk: documentation-only changes need lightweight validation, behavior changes need TDD where practical and post-change assessment, and high-risk flows need security, reliability, rollout, rollback, and observability review.

All durable repository documentation should be written in English.

## Repository Structure

```text
/
  README.md
  CLAUDE.md
  presets/
  templates/
  examples/
  docs/
```

## Core Files

- `CLAUDE.md`: canonical AI agent instructions for new repositories.
- `presets/`: reusable review, implementation, and flow-mapping prompts.
- `templates/`: copy-ready files, review requests, and project setup templates.
- `examples/`: project-specific preset combinations.
- `docs/`: usage, maintenance, project overview, and decision logs.

## How To Use In A New Project

1. Copy `templates/new-project-CLAUDE.md` to `CLAUDE.md` in a target repository.
2. Configure or prompt any AI tools that do not discover `CLAUDE.md` automatically to read it before working.
3. Copy the relevant files from `presets/` into the target repo or paste them into review requests.
4. Copy `templates/project-overview.md` to `docs/project-overview.md` if the target repository does not already have a project overview.

## Adopt These Presets With An AI Agent

Use this prompt from the root of the target repository. It is designed for both new and legacy projects.

Source presets repository:

- `https://github.com/almont/ai-software-engineering`

Target repository:

- The current working directory.

Principle: preserve first, add second. The agent should not overwrite, delete, or simplify existing project knowledge unless you explicitly approve the removal.

Prompt:

```text
Adopt the AI agent presets from `https://github.com/almont/ai-software-engineering` into the current repository.

Treat the current working directory as the target repository.

This may be a legacy project. Preserve existing project knowledge first. Do not overwrite, delete, or simplify existing instructions, architecture notes, commands, docs, or team conventions unless I explicitly approve the removal.

First, inspect the target repository:

- Find existing agent instruction files such as `CLAUDE.md`, `AGENTS.md`, `.github/copilot-instructions.md`, `.cursor/rules`, or similar.
- Find existing documentation under `docs/`, `README.md`, wiki exports, architecture notes, runbooks, ADRs, onboarding docs, or testing docs.
- Identify the project framework, language, architecture, modules, test commands, build commands, local development conventions, deployment notes, and known legacy constraints.
- Summarize what existing guidance must be preserved before proposing edits.

Then inspect the source presets repository:

- Read `templates/new-project-CLAUDE.md`.
- Read `templates/project-overview.md`.
- Read available files under `presets/`, `templates/`, and `examples/`.
- Use only the guidance that is relevant to this target project.

Apply the presets conservatively:

- If `CLAUDE.md` is missing, create it from `templates/new-project-CLAUDE.md` and adapt it to the target project.
- If `CLAUDE.md` already exists, merge useful guidance into it without replacing project-specific content.
- Preserve existing architecture notes, business rules, commands, testing guidance, deployment notes, ownership boundaries, and team conventions.
- If other instruction files exist, do not delete or rewrite them unless I explicitly ask. Instead, recommend whether they should point to `CLAUDE.md` or remain separate.
- If `docs/project-overview.md` is missing, create it from `templates/project-overview.md` and adapt it by inspecting the target repository.
- If `docs/project-overview.md` already exists, update it only where the source template reveals useful missing sections.
- Copy or adapt relevant presets from `presets/` only if they are useful for this target project.
- Copy or adapt relevant request templates from `templates/` only if they are useful for this target project.
- Do not add permission guidance unless explicitly requested.
- Do not blindly overwrite existing files.

When content overlaps or conflicts:

- Prefer target repository-specific guidance over generic source guidance.
- Preserve legacy constraints even when they conflict with idealized architecture.
- Do not introduce DDD layers, DDD terminology, new architectural patterns, structural migrations, or tool changes unless the project already uses them or I explicitly request that migration.
- Explain each conflict and recommend the safest merge.
- Ask before removing existing project-specific instructions.

Before editing, report:

1. Existing instruction and documentation files found in the target repository.
2. Existing project guidance that must be preserved.
3. Source files from `https://github.com/almont/ai-software-engineering` that you plan to use.
4. Files you plan to create or update in the target repository.
5. How you will merge duplicate or overlapping guidance.
6. Any risks or decisions that need approval.

After editing, report:

1. Files changed.
2. What was merged from the source presets.
3. What was preserved from the target repository.
4. What was intentionally left out.
5. Conflicts or trade-offs resolved.
6. Validation performed.
```

## How To Plan A New Feature

1. Start with `templates/new-feature-request.md` to capture the problem, desired outcome, scope, constraints, acceptance criteria, trade-offs, tests, and rollout expectations.
2. Use `presets/new-feature-planning.md` to have an agent produce a Staff Engineer-level plan before implementation.
3. Use `presets/ambiguity-resolution.md` when the plan has meaningful ambiguity or needs a deliberate stress test before implementation.
4. Review the plan for scope, trade-offs, security, reliability, observability, test coverage, rollout, and rollback.
5. Use `presets/test-driven-implementation.md` for behavior-changing implementation work where automated tests are practical.
6. Only then move into implementation using `presets/implementation-guidelines.md`.

## Available Presets

- `presets/engineering-review.md`: staff-level review focused on business impact, architecture, security, reliability, observability, tests, and operational risk.
- `presets/security-review.md`: security review for injection, auth, authorization, sensitive data, SSRF, unsafe upload, webhook spoofing, validation, and rate limits.
- `presets/reliability-review.md`: reliability review for retries, timeouts, idempotency, race conditions, dead-letter queues, partial failures, observability, rollback, and data consistency.
- `presets/test-review.md`: test coverage review for unit, integration, contract, happy path, error path, edge case, and regression coverage.
- `presets/new-feature-planning.md`: Staff Engineer-level feature planning before implementation.
- `presets/change-risk-calibration.md`: lightweight guide for choosing validation depth by change risk.
- `presets/ambiguity-resolution.md`: optional ambiguity-resolution interview for stress-testing plans and resolving decision dependencies before implementation.
- `presets/legacy-change-guidelines.md`: guidance for safe changes in legacy or under-tested projects.
- `presets/post-change-assessment.md`: post-change checklist for tests, security, reliability, compatibility, rollout, and observability.
- `presets/test-driven-implementation.md`: test-first implementation workflow for features, bug fixes, refactors, and behavior changes where automated tests are practical.
- `presets/implementation-guidelines.md`: implementation workflow for feature work and bug fixes.
- `presets/feature-flow-mapping.md`: end-to-end feature flow mapping.
- `presets/event-driven-flow-mapping.md`: producer, consumer, payload, retry, ordering, DLQ, and idempotency mapping.

## Available Templates

- `templates/new-project-CLAUDE.md`: canonical agent instructions for a target repository.
- `templates/project-overview.md`: onboarding-first project overview template for humans and agents, including context diagrams, domains, services, workflows, operations, and governance.
- `templates/new-feature-request.md`: feature request intake template.
- `templates/pr-review-request.md`: PR review request template.
- `templates/security-review-request.md`: security review request template.
- `templates/decision-log-entry.md`: decision log entry template.

## Example Starting Points

- Use `examples/backend-service.md` for backend APIs and services.
- Use `examples/frontend-app.md` for frontend applications.

## Maintenance Rules

Treat `CLAUDE.md` as the canonical source. When standards change:

1. Update `CLAUDE.md`.
2. Update matching files in `templates/`.
3. Update `presets/`, templates, and `examples/` if needed.
4. Review `docs/usage.md` and `docs/maintenance.md`.
5. Update `docs/project-overview.md` when the project shape or workflow changes.
6. Add a decision log entry under `docs/decisions/` for meaningful development decisions.

Keep documentation in English, even when the original request or conversation is in another language.

## Decision Logs

Use `docs/project-overview.md` as the living summary of the repository. Start new project overview files from `templates/project-overview.md`. Use `docs/decisions/` for one decision file per meaningful development decision. Start new entries from `templates/decision-log-entry.md`.

## License

This project is licensed under the MIT License. See `LICENSE` for details.
