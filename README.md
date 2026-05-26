# AI Presets Boilerplate

Reusable AI agent presets for Codex, Claude, GitHub Copilot, and team review workflows.

This repository is intentionally documentation-first. It is a source of truth for agent behavior, review prompts, and safe development permission guidance that can be copied into new projects. There is no install script, package manager, or runtime.

## Purpose

Use this repository to standardize how AI agents work across projects:

- How agents should implement features and fixes.
- How agents should plan new features before implementation.
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
- `docs/`: usage, maintenance, project overview, and decision logs.

## How To Use In A New Project

1. Copy `templates/new-project-AGENTS.md` to `AGENTS.md` in a target repository.
2. Copy `templates/new-project-CLAUDE.md` to `CLAUDE.md` if the project uses Claude.
3. Copy `templates/new-project-copilot-instructions.md` to `.github/copilot-instructions.md` if the project uses GitHub Copilot.
4. Copy the relevant files from `presets/` into the target repo or paste them into review requests.
5. Copy the relevant file from `permissions/` if you want a documented allowlist.

## Pull Files Into A Local Project

Run this from the root of the target repository where you want to apply these presets. The script copies the main project instruction files, stores reusable presets under `docs/ai-presets/`, records the source commit, and prints every file it created.

Existing files are not overwritten. When a destination already exists, the script writes a `.incoming` file so you can review the diff manually.

```bash
set -euo pipefail

SOURCE_REPO="https://github.com/almont/ai-software-engineering.git"
SOURCE_REF="main"
TMP_DIR="$(mktemp -d)"
CREATED_FILES="$(mktemp)"

git clone --depth 1 --branch "$SOURCE_REF" --filter=blob:none --sparse "$SOURCE_REPO" "$TMP_DIR"
git -C "$TMP_DIR" sparse-checkout set templates presets permissions examples

copy_or_incoming() {
  src="$1"
  dest="$2"

  mkdir -p "$(dirname "$dest")"

  if [ -e "$dest" ]; then
    cp "$src" "$dest.incoming"
    echo "$dest.incoming" >> "$CREATED_FILES"
  else
    cp "$src" "$dest"
    echo "$dest" >> "$CREATED_FILES"
  fi
}

copy_or_incoming "$TMP_DIR/templates/new-project-AGENTS.md" "AGENTS.md"
copy_or_incoming "$TMP_DIR/templates/new-project-CLAUDE.md" "CLAUDE.md"
copy_or_incoming "$TMP_DIR/templates/new-project-copilot-instructions.md" ".github/copilot-instructions.md"

mkdir -p docs/ai-presets

for dir in presets permissions templates examples; do
  mkdir -p "docs/ai-presets/$dir"
  find "$TMP_DIR/$dir" -type f | while read -r src; do
    rel="${src#"$TMP_DIR/"}"
    dest="docs/ai-presets/$rel"
    copy_or_incoming "$src" "$dest"
  done
done

git -C "$TMP_DIR" rev-parse HEAD > docs/ai-presets/SOURCE_COMMIT
echo "docs/ai-presets/SOURCE_COMMIT" >> "$CREATED_FILES"

rm -rf "$TMP_DIR"

echo "Created files:"
sort -u "$CREATED_FILES"
rm -f "$CREATED_FILES"

echo
echo "Review changes:"
git status --short
```

After running it, review any `.incoming` files before replacing existing project documentation:

```bash
find . -name "*.incoming" -print
git diff
```

## How To Plan A New Feature

1. Start with `templates/new-feature-request.md` to capture the problem, desired outcome, scope, constraints, acceptance criteria, trade-offs, tests, and rollout expectations.
2. Use `presets/new-feature-planning.md` to have an agent produce a Staff Engineer-level plan before implementation.
3. Review the plan for scope, trade-offs, security, reliability, observability, test coverage, rollout, and rollback.
4. Only then move into implementation using `presets/implementation-guidelines.md`.

## Available Presets

- `presets/engineering-review.md`: staff-level review focused on business impact, architecture, security, reliability, observability, tests, and operational risk.
- `presets/security-review.md`: security review for injection, auth, authorization, sensitive data, SSRF, unsafe upload, webhook spoofing, validation, and rate limits.
- `presets/reliability-review.md`: reliability review for retries, timeouts, idempotency, race conditions, dead-letter queues, partial failures, observability, rollback, and data consistency.
- `presets/test-review.md`: test coverage review for unit, integration, contract, happy path, error path, edge case, and regression coverage.
- `presets/new-feature-planning.md`: Staff Engineer-level feature planning before implementation.
- `presets/implementation-guidelines.md`: implementation workflow for feature work and bug fixes.
- `presets/feature-flow-mapping.md`: end-to-end feature flow mapping.
- `presets/event-driven-flow-mapping.md`: producer, consumer, payload, retry, ordering, DLQ, and idempotency mapping.

## Permission Guides

The permission guides define common local development actions that are usually safe:

- Read, list, and search files.
- Inspect git status, diffs, branches, and logs.
- Run tests, lint, format, typecheck, builds, and local dev servers.
- Use explicit `npm`, `pnpm`, and `yarn` scripts such as tests, linting, typechecking, builds, and local dev servers.
- Use `gh` for non-destructive GitHub workflows.
- Use `docker` and `docker compose` for local inspection such as `ps` and `logs`.

They also define actions that require explicit approval:

- Destructive file or git operations.
- Pushing, merging, tagging, releasing, or deploying.
- Production data access or mutation.
- Secret, token, key, or credential handling.
- Authentication, authorization, permission, infrastructure, or CI/CD changes.
- High-risk business workflow, webhook, or external integration behavior changes.
- Database migrations, schema deletion, or data deletion.
- Docker prune or delete operations.
- Broad package manager script prefixes or Docker lifecycle commands without project-specific review.
- Unknown tool installs or untrusted network commands.

## Example Starting Points

- Use `examples/backend-service.md` for backend APIs and services.
- Use `examples/frontend-app.md` for frontend applications.

## Maintenance Rules

Treat `AGENTS.md` as the canonical source. When standards change:

1. Update `AGENTS.md`.
2. Mirror relevant guidance into `CLAUDE.md`.
3. Condense relevant guidance into `.github/copilot-instructions.md`.
4. Update matching files in `templates/`.
5. Update `presets/`, `permissions/`, and `examples/` if needed.
6. Review `docs/usage.md` and `docs/maintenance.md`.
7. Update `docs/project-overview.md` when the project shape or workflow changes.
8. Add a decision log entry under `docs/decisions/` for meaningful development decisions.

Keep documentation in English, even when the original request or conversation is in another language.

## Decision Logs

Use `docs/project-overview.md` as the living summary of the repository. Use `docs/decisions/` for one decision file per meaningful development decision. Start new entries from `templates/decision-log-entry.md`.

## Design Choice

This repository does not include an apply script yet. Manual copying keeps the first version transparent and easy to audit. If repeated setup becomes painful, an optional script can be added later without changing the documentation model.

## License

This project is licensed under the MIT License. See `LICENSE` for details.
