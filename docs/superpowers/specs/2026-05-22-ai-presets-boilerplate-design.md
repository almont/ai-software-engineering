# AI Presets Boilerplate Design

Historical note: this is the original design artifact for the repository. Use `docs/project-overview.md`, `README.md`, and `docs/maintenance.md` for the current repository state and maintenance workflow.

## Goal

Create a simple documented boilerplate repository for reusable AI agent presets across new projects. The repository will focus on Codex, Claude, and GitHub Copilot instructions, plus team review presets and safe development permission guidance.

## Scope

The repository is documentation-first. It will not include install scripts or automation in the initial version. Users will copy the relevant files or folders into new projects.

In scope:

- Canonical Codex instructions in `AGENTS.md`.
- Claude-compatible instructions in `CLAUDE.md`.
- GitHub Copilot custom instructions in `.github/copilot-instructions.md`.
- Reusable review, reliability, security, testing, implementation, and flow-mapping presets.
- Safe development allowlists for Codex and Claude.
- Copy-ready templates for new repositories.
- Examples for backend and frontend projects.
- Usage and maintenance documentation.

Out of scope:

- Install/apply scripts.
- Package publishing.
- CI/CD automation.
- Runtime prompt execution.

## Repository Structure

```text
/
  README.md
  AGENTS.md
  CLAUDE.md
  .github/
    copilot-instructions.md
  presets/
    engineering-review.md
    security-review.md
    reliability-review.md
    test-review.md
    implementation-guidelines.md
    feature-flow-mapping.md
    event-driven-flow-mapping.md
  permissions/
    codex-allow.md
    claude-allow.md
  templates/
    new-project-AGENTS.md
    new-project-CLAUDE.md
    new-project-copilot-instructions.md
    codex-allow-permissions.md
    claude-allow-permissions.md
    pr-review-request.md
    security-review-request.md
  examples/
    backend-service.md
    frontend-app.md
  docs/
    usage.md
    maintenance.md
```

## Content Model

`AGENTS.md` is the canonical instruction file for Codex and similar agents. It contains engineering review guidelines, implementation workflow, security expectations, testing requirements, and final summary format.

`CLAUDE.md` mirrors the same team standards in Claude-compatible wording. It avoids Codex-specific behavior while preserving the core expectations.

`.github/copilot-instructions.md` is concise and optimized for GitHub Copilot. It focuses on coding standards, tests, security, reliability, and review discipline without long agent workflow sections.

`presets/` stores reusable prompts and review modes. Each preset is self-contained, named by use case, and includes expected focus areas and output format.

`permissions/` documents common safe development actions allowed for Codex and Claude. The allowlists include file inspection, tests, linting, formatting, typechecking, builds, local dev servers, `npm`, `pnpm`, `yarn`, `gh`, `docker`, and `docker compose`. They also define actions requiring explicit approval.

`templates/` provides copy-ready files for new projects. Templates can duplicate canonical instructions when useful so users do not need to assemble files manually.

`examples/` shows how to combine presets for common project types.

`docs/` explains how to use and maintain the boilerplate.

## Permission Policy

Common safe development actions may be allowed by default:

- Read, search, and list repository files.
- Inspect git status, diffs, branches, and logs.
- Run tests, lint, format, typecheck, and builds.
- Run local development servers.
- Use package managers: `npm`, `pnpm`, `yarn`.
- Use GitHub CLI commands for inspection and non-destructive PR/issue workflows.
- Use local Docker commands needed for development, including `docker` and `docker compose`.

Actions requiring explicit approval:

- Destructive file or git operations.
- Pushing, merging, tagging, releasing, or deployment.
- Production data access or mutation.
- Secret, token, key, or credential handling.
- Authentication, authorization, permission, or infrastructure changes.
- High-risk business workflow, webhook, or external integration behavior changes.
- Database migrations, data deletion, or irreversible schema changes.
- Docker prune/delete operations or volume/image/container removal.
- Installing unknown tools or running untrusted network commands.

## Testing and Validation

This boilerplate has no executable application tests. Validation is documentation review:

- `AGENTS.md`, `CLAUDE.md`, and Copilot instructions do not contradict each other.
- Permission allowlists clearly separate safe and approval-required actions.
- Presets have concrete focus areas and expected outputs.
- Templates are copy-ready.
- Examples reference existing presets and templates.
- No secrets or sensitive sample data appear in the repository.

## Risks and Trade-Offs

Duplicating guidance across Codex, Claude, and Copilot can drift over time. The maintenance guide will define a simple rule: update `AGENTS.md` first, then mirror relevant changes into `CLAUDE.md`, Copilot instructions, and templates.

Keeping the first version script-free makes adoption easy but requires manual copying. A future script can be added if repeated setup becomes painful.

## Approval

The user approved the simple documented boilerplate approach with Codex, Claude, GitHub Copilot, reusable team presets, and common safe development allow permissions.
