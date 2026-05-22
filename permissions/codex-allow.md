# Codex Safe Development Allowlist

These actions are commonly safe for local development and may be allowed by default when working in a repository.

## Safe To Allow

- Read, list, and search repository files.
- Inspect git status, diffs, branches, and logs.
- Run tests.
- Run linting.
- Run formatting.
- Run typechecks.
- Run local builds.
- Run local development servers.
- Use package managers for project scripts and dependency inspection: `npm`, `pnpm`, `yarn`.
- Use GitHub CLI for inspection and non-destructive issue or pull request workflows: `gh`.
- Use local Docker development commands: `docker`, `docker compose`.

## Require Explicit Approval

- Destructive file operations.
- Destructive git operations.
- Pushing, merging, tagging, releasing, or deploying.
- Accessing or changing production data.
- Handling secrets, tokens, keys, or credentials.
- Authentication, authorization, permission, infrastructure, or CI/CD changes.
- Payment, billing, webhook, or money-movement behavior changes.
- Database migrations, schema deletion, or data deletion.
- Docker prune operations.
- Deleting Docker volumes, images, networks, or containers.
- Installing unknown tools or running untrusted network commands.

## Suggested Command Prefixes

Useful safe prefixes:

- `npm test`
- `npm run`
- `pnpm test`
- `pnpm run`
- `yarn test`
- `yarn run`
- `gh pr view`
- `gh pr diff`
- `gh pr checks`
- `gh issue view`
- `docker ps`
- `docker compose ps`
- `docker compose up`
- `docker compose logs`

Avoid broad allow rules for arbitrary shells, interpreters, destructive commands, or commands that can mutate production systems.

