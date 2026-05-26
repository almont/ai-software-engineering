# 0003: Tighten Permissions And Document Validation

## Status

Accepted

## Date

2026-05-26

## Context

The repository provides reusable agent instructions and permission guidance for new projects. The existing permission allowlists included broad package manager script prefixes and Docker lifecycle commands that could be unsafe when copied into repositories with deployment, migration, release, or destructive scripts.

The repository also needed a lightweight way to catch documentation consistency gaps, such as references to files that do not exist. Because this repository is documentation-first and intentionally script-free, validation needs to catch these issues without introducing runtime tooling.

## Decision

Tighten permission guidance to prefer explicit, reviewed command prefixes. Package manager commands should name known project scripts such as test, lint, typecheck, build, and dev. Docker inspection commands can remain safe defaults, while Docker lifecycle commands require approval unless a project-specific allow rule has been reviewed.

Keep examples generic and avoid domain-specific example categories unless they are broadly useful across projects.

Document lightweight validation commands in `docs/maintenance.md` instead of adding an executable script or package dependency.

Mark the original Superpowers spec and plan as historical artifacts so maintainers use the current overview and maintenance docs for repository state.

## Consequences

This reduces the chance that copied allowlists accidentally permit deployments, migrations, releases, destructive scripts, or Docker mutations.

The trade-off is that teams may need to add project-specific allow rules for safe local service startup. That extra step is intentional for higher-risk commands.

Keeping validation as a checklist preserves the script-free design but relies on maintainers to run the commands during documentation changes.

## Follow-Up

If the repository becomes shared across many teams, consider adding optional CI or a local validation script to check broken Markdown references and unfinished markers automatically.
