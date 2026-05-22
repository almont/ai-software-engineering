# Claude Safe Development Allowlist

These actions are commonly safe for local development and may be allowed by default when Claude works in a repository.

## Safe To Allow

- Read, list, and search repository files.
- Inspect git status, diffs, branches, and logs.
- Run tests, linting, formatting, typechecks, builds, and local dev servers.
- Use package managers for project scripts and dependency inspection: `npm`, `pnpm`, `yarn`.
- Use GitHub CLI for inspection and non-destructive pull request or issue workflows: `gh`.
- Use local Docker development commands: `docker`, `docker compose`.

## Require Explicit Approval

- Destructive file or git operations.
- Pushing, merging, tagging, releasing, or deploying.
- Accessing or mutating production data.
- Reading, writing, or transmitting secrets, tokens, keys, or credentials.
- Authentication, authorization, permission, infrastructure, or CI/CD changes.
- Payment, billing, webhook, or money-movement behavior changes.
- Database migrations, schema deletion, or data deletion.
- Docker prune commands.
- Deleting Docker volumes, images, networks, or containers.
- Installing unknown tools or running untrusted network commands.

## Suggested Permission Groups

Allow common local development commands by category:

- File inspection.
- Git inspection.
- Test, lint, format, typecheck, and build.
- Package manager project scripts.
- GitHub CLI read-only workflows.
- Local Docker development.

Do not allow broad shell execution, destructive operations, production mutation, or secret handling without review.

