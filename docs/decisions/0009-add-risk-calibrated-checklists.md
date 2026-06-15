# Add Risk-Calibrated Checklists

## Status

Accepted

## Date

2026-06-15

## Context

The repository now includes strong guidance for TDD, post-change validation, legacy architecture protection, security, reliability, and observability. As those expectations grew, the main risk became operational weight: small changes should not require the same process as high-risk payment, webhook, authentication, or async changes.

The guidance also needed reusable checklists so agents do not improvise post-change assessment or legacy-code handling.

## Decision

Add three reusable presets:

- `presets/change-risk-calibration.md` to choose the right level of rigor by risk.
- `presets/post-change-assessment.md` to standardize tests, validation, security, reliability, compatibility, rollout, and observability checks after changes.
- `presets/legacy-change-guidelines.md` to guide safe work in legacy or under-tested projects without opportunistic architecture migration.

Reference these presets from canonical agent instructions, templates, implementation and planning presets, usage docs, README, examples, and the project overview.

Update maintenance guidance to explicitly check for drift between canonical instructions and mirrored tool/template documentation.

## Consequences

Agents get small, reusable workflows instead of longer ad hoc guidance in every prompt. This should reduce superficial security and reliability summaries while keeping low-risk documentation changes lightweight.

The trade-off is a larger preset catalog. The usage docs and examples must stay current so teams know which presets to use.

## Follow-Up

If the preset catalog continues to grow, consider grouping presets by category or adding an index file.
