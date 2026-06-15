# Remove Permissions Directory

## Status

Accepted

## Date

2026-06-15

## Context

The repository included a top-level `permissions/` directory with Codex and Claude allowlist guidance. Those files did not grant or enforce permissions by themselves; they were only policy text.

Keeping that policy text in a top-level `permissions/` directory could imply that copying the directory enables permissions automatically.

## Decision

Remove the top-level `permissions/` directory.

Keep permission guidance as copy-ready templates under `templates/`:

- `templates/codex-allow-permissions.md`
- `templates/claude-allow-permissions.md`

Update usage, overview, README, examples, maintenance guidance, and the local import workflow so permission guidance is described as policy text rather than an active permission mechanism.

## Consequences

This reduces confusion about what the repository can enforce. Permission guidance remains available, but teams must intentionally copy or adapt it into their agent or tool configuration.

The trade-off is that permission guidance is no longer grouped in its own top-level directory. This is acceptable because it behaves like the other copy-ready templates.

## Follow-Up

If this repository later adds real tool-specific permission configuration, document the mechanism separately from policy templates.
