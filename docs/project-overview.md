# Project Overview

This document is the living overview for the AI Presets Boilerplate repository. Update it whenever a meaningful development decision, workflow change, feature, preset, template, or repository structure change is introduced.

## Purpose

This repository provides reusable AI agent instructions, presets, templates, examples, and team review workflows centered on one canonical `CLAUDE.md` file. It standardizes how agents plan work, implement features, review code, reason about trade-offs, and preserve project-specific guidance.

The repository is documentation-first. It has no runtime, package manager, or install script.

## Agent Operating Model

Agents should act as experienced Staff Engineers. They should optimize for:

- Clarity.
- Automated tests.
- Low coupling.
- Maintainability.
- Scale.
- Operational safety.
- Backward compatibility.
- System sustainability.
- Explicit trade-off analysis.

Agents should think before coding by stating assumptions, surfacing ambiguity, and asking when requirements are unclear. They should prefer the simplest solution that fits the request, make surgical changes only, and turn tasks into verifiable goals with checks for multi-step work.

Agents should use DDD only when it clarifies meaningful business rules, domain boundaries, or invariants in a project that already uses or explicitly asks for that style. In legacy projects, agents should not introduce DDD layers, new architectural patterns, structural migrations, or DDD terminology unless the existing architecture already uses them or the user explicitly requests that migration.

Agents should use SOLID to evaluate code they are already changing, not to justify broad refactors or new architecture. They should use DRY to protect shared business rules, invariants, calculations, validation, policies, and workflows from drifting, not to extract similar-looking code prematurely.

Agents should read `docs/project-overview.md` when present. If it is missing in a target project, they should inspect the project and suggest creating one before or alongside meaningful implementation work.

After code changes or implementation, agents should run applicable tests or validation checks and perform a brief security and reliability assessment. For frontend changes, agents should include browser-based validation when user flows, routing, forms, visual layout, responsiveness, authentication, checkout, onboarding, or other UI behavior is affected. If the project uses Playwright, Cypress, or another end-to-end framework, agents should run related tests for affected flows when practical.

For feature work, bug fixes, refactors, and behavior changes, agents should use test-driven development by default when automated tests are practical. Documentation-only changes, configuration-only changes, throwaway prototypes, generated code, or work where automated tests are not practical should explain the exception and use the smallest reliable reproduction available.

Agents should calibrate rigor to risk: documentation-only changes need lightweight validation, behavior changes need TDD where practical and post-change assessment, and high-risk flows need security, reliability, rollout, rollback, and observability review.

All durable repository documentation must be written in English.

## Core Repository Areas

- `CLAUDE.md`: canonical AI agent instructions.
- `presets/`: reusable prompts for planning, implementation, review, reliability, security, tests, and flow mapping.
- `templates/`: copy-ready request templates, project setup files, and project overview template.
- `examples/`: project-type examples showing which presets and templates to combine.
- `docs/`: usage, maintenance, project overview, and decision logs.

## Main Workflows

### New Project Setup

Use `templates/new-project-CLAUDE.md` to copy canonical agent instructions into a new repository. Configure or prompt tools that do not discover `CLAUDE.md` automatically to read it before working.

Use `templates/project-overview.md` to create an onboarding-first `docs/project-overview.md` in target repositories that do not already have one. The template helps humans and agents map purpose, system context, domains, services, workflows, repository structure, local development, operations, tests, and governance.

The README includes an agent-driven adoption prompt for applying these presets to an existing local repository. The prompt tells agents to inspect the target repository first, preserve legacy project knowledge, merge duplicate guidance conservatively, and avoid blind overwrites.

### New Feature Planning

Use `templates/new-feature-request.md` to capture the feature request. Use `presets/new-feature-planning.md` to have an agent produce a Staff Engineer-level plan before implementation. Move to `presets/implementation-guidelines.md` only after scope, trade-offs, tests, security, reliability, observability, rollout, and rollback have been reviewed.

Use `presets/ambiguity-resolution.md` as an optional ambiguity-resolution workflow when a plan needs deliberate stress-testing. The workflow asks one focused question at a time, recommends an answer, and resolves decision dependencies before implementation.

Use `presets/test-driven-implementation.md` for behavior-changing implementation work where automated tests are practical.

Use `presets/change-risk-calibration.md` when the required validation depth is unclear. Use `presets/legacy-change-guidelines.md` for legacy or under-tested projects. Use `presets/post-change-assessment.md` after code changes or meaningful configuration changes.

### Reviews

Use review presets in `presets/` to focus agents on engineering quality, security, reliability, tests, and event-driven or feature flow mapping.

### Documentation Validation

Use the lightweight validation checklist in `docs/maintenance.md` for documentation changes. The repository remains script-free; validation is performed with standard file listing and search commands.

## Documentation Governance

Every meaningful development decision should create a decision log entry in `docs/decisions/`.

Every meaningful feature or workflow change should update this overview when it changes:

- Repository purpose.
- Agent behavior.
- Workflow.
- Directory structure.
- Security model.
- Maintenance rules.
- Important trade-offs.

Use `templates/decision-log-entry.md` when adding new decision files.

## Current Design Decisions

- The repository is documentation-first and script-free.
- `CLAUDE.md` is the canonical source for agent behavior across AI tools.
- Durable documentation must be written in English.
- Agents operate with Staff Engineer judgment.
- Agents must think before coding, state assumptions, surface ambiguity, and avoid silent interpretation when requirements are unclear.
- Legacy projects should not receive DDD layers, new architectural patterns, structural migrations, or DDD terminology unless the existing architecture already uses them or the user explicitly requests that migration.
- SOLID should evaluate changed code, not justify broad refactors or new architecture.
- DRY should protect shared business rules, invariants, calculations, validation, policies, and workflows from drifting, not extract similar-looking code prematurely.
- Agents should suggest creating `docs/project-overview.md` when it is missing in a target project.
- Meaningful ambiguity can be handled with the optional `presets/ambiguity-resolution.md` workflow before implementation.
- Agents prioritize minimum necessary implementation, avoid speculative flexibility, and keep changes surgical.
- Code changes and implementations should be followed by related tests or validation checks plus a brief security and reliability assessment.
- Frontend changes that affect user flows, routing, forms, visual layout, responsiveness, authentication, checkout, onboarding, or other UI behavior should include browser-based validation; when Playwright, Cypress, or another end-to-end framework exists, agents should run related tests for affected flows when practical.
- Test-driven development is the default for feature work, bug fixes, refactors, and behavior changes where automated tests are practical.
- Rigor should scale to change risk through reusable calibration and post-change assessment presets.
- Multi-step execution should define verifiable success criteria and checks.
- Non-trivial work requires explicit trade-off analysis.
- New feature requests have both a human intake template and an agent planning preset.
- Development decisions are tracked as one file per decision under `docs/decisions/`.
- New project overview files should start from `templates/project-overview.md`, which is optimized for human onboarding and agent orientation through practical sections and Mermaid diagrams.
- Documentation validation is maintained as a lightweight checklist rather than a runtime test suite or apply script.
- The local adoption workflow uses an agent prompt that preserves target repository knowledge first, then merges relevant presets conservatively.
- Tool-specific instruction files such as `AGENTS.md` and `.github/copilot-instructions.md` are intentionally not maintained; tools should be pointed at `CLAUDE.md` instead.
