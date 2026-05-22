# Billing and Payments Example

Recommended files to copy:

- `templates/new-project-AGENTS.md` to `AGENTS.md`.
- `templates/new-project-CLAUDE.md` to `CLAUDE.md`.
- `templates/new-project-copilot-instructions.md` to `.github/copilot-instructions.md`.
- `permissions/codex-allow.md` or `permissions/claude-allow.md`.

Recommended presets:

- `presets/engineering-review.md`.
- `presets/security-review.md`.
- `presets/reliability-review.md`.
- `presets/test-review.md`.
- `presets/event-driven-flow-mapping.md`.

Extra review focus:

- Idempotency keys.
- Duplicate webhook delivery.
- Race conditions.
- Monetary data consistency.
- Retry behavior and dead-letter queues.
- Audit logs.
- Sensitive data in logs.
- Rollback strategy.

