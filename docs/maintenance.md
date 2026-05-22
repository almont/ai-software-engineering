# Maintenance

Keep this repository consistent by treating `AGENTS.md` as the canonical source.

All documentation in this repository must be written in English. If a user provides instructions in another language, translate the durable documentation into English while preserving the intent.

## Update Order

1. Update `AGENTS.md`.
2. Mirror relevant guidance into `CLAUDE.md`.
3. Condense relevant guidance into `.github/copilot-instructions.md`.
4. Update matching files in `templates/`.
5. Update `presets/`, `permissions/`, and `examples/` if the change affects them.
6. Review `docs/usage.md` if setup steps changed.

## Consistency Checklist

- Codex, Claude, and Copilot instructions do not contradict each other.
- All documentation is in English.
- Agent instructions preserve the Staff Engineer posture.
- Copilot instructions remain concise.
- Permission allowlists separate safe local development from approval-required actions.
- Presets include concrete focus areas and output expectations.
- Templates are copy-ready.
- Examples reference existing files.
- No secrets, tokens, credentials, personal data, or payment data appear in examples.

## Versioning

For small teams, use git history as the version log. If the presets become shared across many teams, add a `CHANGELOG.md` later.
