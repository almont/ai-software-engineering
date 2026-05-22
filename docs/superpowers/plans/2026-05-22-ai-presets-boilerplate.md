# AI Presets Boilerplate Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a documentation-first boilerplate repository for Codex, Claude, GitHub Copilot, team AI presets, and safe development permission guidance.

**Architecture:** The repository is a static documentation template. Root instruction files define agent behavior, `presets/` stores reusable prompts, `permissions/` stores safe allowlists, `templates/` stores copy-ready files, and `examples/` shows project-specific combinations.

**Tech Stack:** Markdown files, Git repository metadata, no runtime dependencies.

---

## File Structure

- Create `README.md`: overview, repository map, quick start.
- Create `AGENTS.md`: canonical Codex instructions.
- Create `CLAUDE.md`: Claude-compatible instructions.
- Create `.github/copilot-instructions.md`: concise GitHub Copilot instructions.
- Create `presets/*.md`: reusable review, implementation, and flow mapping prompts.
- Create `permissions/*.md`: safe development allowlists.
- Create `templates/*.md`: copy-ready project instructions and request prompts.
- Create `examples/*.md`: backend, frontend, and billing/payment examples.
- Create `docs/usage.md`: how to use files in new projects.
- Create `docs/maintenance.md`: how to update and keep files aligned.

## Task 1: Scaffold Repository Files

**Files:**
- Create: all files listed in File Structure

- [ ] **Step 1: Create directories**

Run:

```bash
mkdir -p .github presets permissions templates examples docs
```

Expected: command exits with code 0.

- [ ] **Step 2: Add Markdown files**

Create the approved Markdown files with concrete content. Keep all files ASCII. Do not add install scripts or package files.

- [ ] **Step 3: Verify file list**

Run:

```bash
find . -maxdepth 3 -type f | sort
```

Expected: output includes root instructions, `.github/copilot-instructions.md`, preset files, permission files, template files, examples, docs, and superpowers spec/plan files.

## Task 2: Validate Documentation Consistency

**Files:**
- Read: `AGENTS.md`
- Read: `CLAUDE.md`
- Read: `.github/copilot-instructions.md`
- Read: `permissions/codex-allow.md`
- Read: `permissions/claude-allow.md`

- [ ] **Step 1: Check no unfinished markers or sample credentials**

Run:

```bash
rg -n "UNFINISHED|PLACEHOLDER|REPLACE_ME|sample credential" .
```

Expected: no matches except intentional examples, if any. Remove any accidental unfinished marker or sensitive sample.

- [ ] **Step 2: Check instruction alignment**

Review manually:

- `AGENTS.md` and `CLAUDE.md` must share the same engineering, test, security, reliability, and summary expectations.
- Copilot instructions must be shorter and avoid Codex/Claude-specific workflow language.
- Permission docs must list safe common development commands and approval-required actions.

- [ ] **Step 3: Check permission boundaries**

Confirm these are allowed:

- file read/search/list
- tests, lint, format, typecheck, build
- local dev servers
- `npm`, `pnpm`, `yarn`
- `gh`
- `docker`, `docker compose`
- non-destructive git inspection

Confirm these require approval:

- destructive file/git actions
- push, merge, release, deploy
- secrets or credentials
- auth/permissions
- payment/billing/webhook behavior
- DB migrations or deletion
- Docker prune/delete operations
- unknown tool installs or untrusted network commands

## Task 3: Initialize and Verify Git Repository

**Files:**
- Modify: `.git/` metadata through `git init`

- [ ] **Step 1: Initialize git**

Run:

```bash
git init
```

Expected: repository initializes successfully.

- [ ] **Step 2: Inspect status**

Run:

```bash
git status --short
```

Expected: all created files show as untracked.

- [ ] **Step 3: Optional first commit**

Run only if user wants a commit:

```bash
git add .
git commit -m "chore: add ai presets boilerplate"
```

Expected: commit succeeds.

## Self-Review

Spec coverage: plan covers all approved files, safe permissions, docs-only scope, validation, and git initialization.

Placeholder scan: no placeholder instructions remain.

Type consistency: no runtime types or APIs.
