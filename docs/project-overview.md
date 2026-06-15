# Project Overview

This document is the living overview for the AI Presets Boilerplate repository. Update it whenever a meaningful development decision, workflow change, feature, preset, template, or repository structure change is introduced.

## Purpose

This repository provides reusable AI agent presets for Codex, Claude, GitHub Copilot, and team review workflows. It standardizes how agents plan work, implement features, review code, reason about trade-offs, and document safe development permission guidance.

Permission guidance is policy text only. It does not grant or enforce tool permissions by itself.

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

In legacy projects, agents should not introduce DDD layers, new architectural patterns, or structural migrations unless the existing architecture already uses them or the user explicitly requests that migration.

Agents should read `docs/project-overview.md` when present. If it is missing in a target project, they should inspect the project and suggest creating one before or alongside meaningful implementation work.

After code changes or implementation, agents should run applicable tests or validation checks and perform a brief security and reliability assessment.

For feature work, bug fixes, refactors, and behavior changes, agents should use test-driven development by default when automated tests are practical. Documentation-only changes, configuration-only changes, throwaway prototypes, generated code, or work where automated tests are not practical should explain the exception and use the closest validation available.

Agents should calibrate rigor to risk: documentation-only changes need lightweight validation, behavior changes need TDD where practical and post-change assessment, and high-risk flows need security, reliability, rollout, rollback, and observability review.

All durable repository documentation must be written in English.

## Core Repository Areas

- `AGENTS.md`: canonical instructions for Codex and similar coding agents.
- `CLAUDE.md`: Claude-compatible project instructions.
- `.github/copilot-instructions.md`: concise GitHub Copilot custom instructions.
- `presets/`: reusable prompts for planning, implementation, review, reliability, security, tests, and flow mapping.
- `templates/`: copy-ready request templates, project setup files, and permission guidance templates.
- `examples/`: project-type examples showing which presets and templates to combine.
- `docs/`: usage, maintenance, project overview, and decision logs.

## Main Workflows

### New Project Setup

Use the `templates/new-project-*` files to copy agent instructions into a new repository. Add permission guidance from `templates/*-allow-permissions.md` when the team wants explicit allowlist policy text.

The README includes a shell snippet for applying these presets to an existing local repository. The snippet copies files directly into the target repository structure, writes `.incoming` files instead of overwriting existing files, and records the source repository commit in `docs/ai-presets-source.md`.

### New Feature Planning

Use `templates/new-feature-request.md` to capture the feature request. Use `presets/new-feature-planning.md` to have an agent produce a Staff Engineer-level plan before implementation. Move to `presets/implementation-guidelines.md` only after scope, trade-offs, tests, security, reliability, observability, rollout, and rollback have been reviewed.

Use `presets/grill-me.md` as an optional ambiguity-resolution workflow when a plan needs deliberate stress-testing. The workflow asks one focused question at a time, recommends an answer, and resolves decision dependencies before implementation.

Use `presets/test-driven-implementation.md` for behavior-changing implementation work where automated tests are practical.

Use `presets/change-risk-calibration.md` when the required validation depth is unclear. Use `presets/legacy-change-guidelines.md` for legacy or under-tested projects. Use `presets/post-change-assessment.md` after code changes or meaningful configuration changes.

### Reviews

Use review presets in `presets/` to focus agents on engineering quality, security, reliability, tests, and event-driven or feature flow mapping.

### Permissions

Use `templates/codex-allow-permissions.md` and `templates/claude-allow-permissions.md` to document common safe local development actions and actions requiring explicit approval.

Permission guides should prefer explicit command prefixes over broad tool prefixes. Package manager commands should name reviewed scripts such as test, lint, typecheck, build, and dev. Docker commands that inspect local state are generally safer than Docker lifecycle commands, which should require approval unless a project-specific allow rule has been reviewed.

### Documentation Validation

Use the lightweight validation checklist in `docs/maintenance.md` for documentation changes. The repository remains script-free; validation is performed with standard file listing and search commands.

## Documentation Governance

Every meaningful development decision should create a decision log entry in `docs/decisions/`.

Every meaningful feature or workflow change should update this overview when it changes:

- Repository purpose.
- Agent behavior.
- Workflow.
- Directory structure.
- Permission policy.
- Maintenance rules.
- Important trade-offs.

Use `templates/decision-log-entry.md` when adding new decision files.

## Current Design Decisions

- The repository is documentation-first and script-free.
- `AGENTS.md` is the canonical source for agent behavior.
- Durable documentation must be written in English.
- Agents operate with Staff Engineer judgment.
- Agents must think before coding, state assumptions, surface ambiguity, and avoid silent interpretation when requirements are unclear.
- Legacy projects should not receive DDD layers, new architectural patterns, or structural migrations unless the existing architecture already uses them or the user explicitly requests that migration.
- Agents should suggest creating `docs/project-overview.md` when it is missing in a target project.
- Meaningful ambiguity can be handled with the optional `presets/grill-me.md` workflow before implementation.
- Agents prioritize minimum necessary implementation, avoid speculative flexibility, and keep changes surgical.
- Code changes and implementations should be followed by related tests or validation checks plus a brief security and reliability assessment.
- Test-driven development is the default for feature work, bug fixes, refactors, and behavior changes where automated tests are practical.
- Rigor should scale to change risk through reusable calibration and post-change assessment presets.
- Multi-step execution should define verifiable success criteria and checks.
- Non-trivial work requires explicit trade-off analysis.
- New feature requests have both a human intake template and an agent planning preset.
- Development decisions are tracked as one file per decision under `docs/decisions/`.
- Permission guidance lives as copy-ready templates and prefers explicit, reviewed command prefixes over broad package manager or Docker lifecycle permissions.
- Documentation validation is maintained as a lightweight checklist rather than a runtime test suite or apply script.
- The local import workflow applies files directly to their expected target paths and uses `.incoming` files for reviewable conflicts.
- Permission guidance is kept under `templates/` because it is policy text and does not grant permissions by itself.
