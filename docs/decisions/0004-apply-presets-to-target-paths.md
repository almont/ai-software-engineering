# 0004: Apply Presets To Target Paths

## Status

Accepted

## Date

2026-05-26

## Context

The README includes a shell snippet for pulling this repository's presets into another local repository. The first version stored reusable files under `docs/ai-presets/`, which worked as a vendored reference copy but did not directly apply the repository structure users need.

Because the script already protects existing files by writing `.incoming` copies, it can safely place files in their expected target paths.

## Decision

Change the documented local import workflow to copy files directly into the target repository structure:

- `AGENTS.md`
- `CLAUDE.md`
- `.github/copilot-instructions.md`
- `presets/`
- `permissions/`
- `templates/`
- `examples/`

When a destination file already exists, write a sibling `.incoming` file instead of overwriting it.

Record the source repository, ref, and commit in `docs/ai-presets-source.md`.

## Consequences

The import workflow now behaves like an application step instead of a vendoring step, so users can review exactly how the presets would affect their repository.

The trade-off is that target repositories will receive top-level preset directories. This is intentional because those directories are the structure expected by the documentation and examples.

## Follow-Up

If repeated imports become common, consider turning the documented snippet into an optional script with `--dry-run`, `--overwrite`, and component selection flags.
