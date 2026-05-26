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
- Use package managers only for explicit, reviewed project scripts such as test, lint, typecheck, build, and dev server commands.
- Use GitHub CLI for inspection and non-destructive issue or pull request workflows: `gh`.
- Use local Docker inspection commands such as `docker ps`, `docker logs`, `docker compose ps`, and `docker compose logs`.

## Require Explicit Approval

- Destructive file operations.
- Destructive git operations.
- Pushing, merging, tagging, releasing, or deploying.
- Accessing or changing production data.
- Handling secrets, tokens, keys, or credentials.
- Authentication, authorization, permission, infrastructure, or CI/CD changes.
- High-risk business workflow, webhook, or external integration behavior changes.
- Database migrations, schema deletion, or data deletion.
- Docker prune operations.
- Deleting Docker volumes, images, networks, or containers.
- Starting or rebuilding Docker services unless the project has a reviewed, project-specific allow rule.
- Installing unknown tools or running untrusted network commands.

## Suggested Command Prefixes

Useful safe prefixes:

- `npm test`
- `npm run test`
- `npm run lint`
- `npm run typecheck`
- `npm run build`
- `npm run dev`
- `pnpm test`
- `pnpm run test`
- `pnpm run lint`
- `pnpm run typecheck`
- `pnpm run build`
- `pnpm run dev`
- `yarn test`
- `yarn run test`
- `yarn run lint`
- `yarn run typecheck`
- `yarn run build`
- `yarn run dev`
- `gh pr view`
- `gh pr diff`
- `gh pr checks`
- `gh issue view`
- `docker ps`
- `docker logs`
- `docker compose ps`
- `docker compose logs`

Avoid broad allow rules for arbitrary shells, interpreters, package manager script prefixes, destructive commands, Docker lifecycle commands, or commands that can mutate production systems.
