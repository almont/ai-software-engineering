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

In legacy projects, agents should not introduce DDD layers, new architectural patterns, or structural migrations unless the existing architecture already uses them or the user explicitly requests that migration.

Agents should read `docs/project-overview.md` when present. If it is missing, they should inspect the project and suggest creating one before or alongside meaningful implementation work.

After code changes or implementation, agents should run applicable tests or validation checks and perform a brief security and reliability assessment. For frontend changes, agents should include browser-based validation when user flows, routing, forms, visual layout, responsiveness, authentication, checkout, onboarding, or other UI behavior is affected. If the project uses Playwright, Cypress, or another end-to-end framework, agents should run related tests for affected flows when practical.

For feature work, bug fixes, refactors, and behavior changes, agents should use test-driven development by default when automated tests are practical: write or identify a failing test or reproduction first, make the smallest passing change, then refactor while tests stay green.

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

## Pull Files Into A Local Project

Run this from the root of the target repository where you want to apply these presets. The script copies files directly into the expected project structure, records the source commit, and prints every file it created.

Existing files are not overwritten. When a destination already exists, the script writes a `.incoming` file so you can review the diff manually.

```bash
set -euo pipefail

SOURCE_REPO="https://github.com/almont/ai-software-engineering.git"
SOURCE_REF="main"
TMP_DIR="$(mktemp -d)"
CREATED_FILES="$(mktemp)"

git clone --depth 1 --branch "$SOURCE_REF" --filter=blob:none --sparse "$SOURCE_REPO" "$TMP_DIR"
git -C "$TMP_DIR" sparse-checkout set templates presets examples
SOURCE_COMMIT="$(git -C "$TMP_DIR" rev-parse HEAD)"

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

copy_or_incoming "$TMP_DIR/templates/new-project-CLAUDE.md" "CLAUDE.md"

for dir in presets templates examples; do
  find "$TMP_DIR/$dir" -type f | while read -r src; do
    rel="${src#"$TMP_DIR/"}"
    copy_or_incoming "$src" "$rel"
  done
done

SOURCE_DOC="$(mktemp)"
cat > "$SOURCE_DOC" <<EOF
# AI Presets Source

- Repository: $SOURCE_REPO
- Ref: $SOURCE_REF
- Commit: $SOURCE_COMMIT
EOF

copy_or_incoming "$SOURCE_DOC" "docs/ai-presets-source.md"

rm -rf "$TMP_DIR"
rm -f "$SOURCE_DOC"

echo "Created files:"
sort -u "$CREATED_FILES"
rm -f "$CREATED_FILES"

echo
echo "Review changes:"
git status --short
```

After running it, review both newly created files and `.incoming` conflict files:

```bash
git status --short
find . -name "*.incoming" -print
git diff
```

The `Created files:` output from the script lists every file written during the run. The `find` command only lists `.incoming` files created because a destination file already existed.

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

## Design Choice

This repository does not include an apply script yet. Manual copying keeps the first version transparent and easy to audit. If repeated setup becomes painful, an optional script can be added later without changing the documentation model.

## License

This project is licensed under the MIT License. See `LICENSE` for details.
