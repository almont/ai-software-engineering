# Claude Safe Development Allowlist

These actions are commonly safe for local development and may be allowed by default when Claude works in a repository.

## Safe To Allow

- Read, list, and search repository files.
- Inspect git status, diffs, branches, and logs.
- Run tests, linting, formatting, typechecks, builds, and local dev servers.
- Use package managers only for explicit, reviewed project scripts such as test, lint, typecheck, build, and dev server commands.
- Use GitHub CLI for inspection and non-destructive pull request or issue workflows: `gh`.
- Use local Docker inspection commands such as `docker ps`, `docker logs`, `docker compose ps`, and `docker compose logs`.

## Require Explicit Approval

- Destructive file or git operations.
- Pushing, merging, tagging, releasing, or deploying.
- Accessing or mutating production data.
- Reading, writing, or transmitting secrets, tokens, keys, or credentials.
- Authentication, authorization, permission, infrastructure, or CI/CD changes.
- High-risk business workflow, webhook, or external integration behavior changes.
- Database migrations, schema deletion, or data deletion.
- Docker prune commands.
- Deleting Docker volumes, images, networks, or containers.
- Starting or rebuilding Docker services unless the project has a reviewed, project-specific allow rule.
- Installing unknown tools or running untrusted network commands.

## Suggested Permission Groups

Allow common local development commands by category:

- File inspection.
- Git inspection.
- Test, lint, format, typecheck, and build.
- Explicit package manager project scripts.
- GitHub CLI read-only workflows.
- Local Docker inspection.

Do not allow broad shell execution, package manager script prefixes, Docker lifecycle commands, destructive operations, production mutation, or secret handling without review.
