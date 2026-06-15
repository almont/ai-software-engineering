# Maintenance

Keep this repository consistent by treating `AGENTS.md` as the canonical source.

All documentation in this repository must be written in English. If a user provides instructions in another language, translate the durable documentation into English while preserving the intent.

## Update Order

1. Update `AGENTS.md`.
2. Mirror relevant guidance into `CLAUDE.md`.
3. Condense relevant guidance into `.github/copilot-instructions.md`.
4. Update matching files in `templates/`.
5. Update `presets/`, permission guidance templates, and `examples/` if the change affects them.
6. Update `docs/project-overview.md` if the project shape, workflow, permission policy, or governance model changed.
7. Create a decision log entry under `docs/decisions/` for meaningful development decisions.
8. Review `docs/usage.md` if setup steps changed.

## Consistency Checklist

- Codex, Claude, and Copilot instructions do not contradict each other.
- New canonical guidance appears in the matching Claude, Copilot, template, usage, README, and overview files where relevant.
- All documentation is in English.
- Agent instructions preserve the Staff Engineer posture.
- Copilot instructions remain concise.
- Permission guidance templates separate safe local development from approval-required actions.
- Presets include concrete focus areas and output expectations.
- Templates are copy-ready.
- Examples reference existing files.
- `docs/project-overview.md` reflects current repository behavior.
- Meaningful development decisions have one decision log entry under `docs/decisions/`.
- No secrets, tokens, credentials, personal data, regulated data, or other sensitive data appear in examples.

## Documentation Validation

This repository has no runtime test suite. For documentation changes, run lightweight validation before finishing:

```bash
find . -maxdepth 3 -type f | sort
rg -n "[U]NFINISHED|[P]LACEHOLDER|[R]EPLACE_ME|[s]ample credential" . -g "*.md" -g "!docs/superpowers/**"
rg -n "examples/.*\\.md" README.md docs examples templates presets AGENTS.md CLAUDE.md
```

Review the output for:

- References to files that do not exist.
- Unfinished markers or accidental example secrets.
- New examples, presets, templates, or permission guidance missing from usage or overview docs.
- Drift between `AGENTS.md`, `CLAUDE.md`, `.github/copilot-instructions.md`, matching templates, `README.md`, `docs/usage.md`, and `docs/project-overview.md` when canonical behavior changes.

## Decision Logs

Use `templates/decision-log-entry.md` when creating new entries under `docs/decisions/`.

Create a decision log entry for changes that affect:

- Agent behavior.
- Repository structure.
- New project or new feature workflows.
- Permission policy.
- Review standards.
- Documentation governance.
- Operational or maintenance trade-offs.

## Versioning

For small teams, use git history as the version log. If the presets become shared across many teams, add a `CHANGELOG.md` later.
