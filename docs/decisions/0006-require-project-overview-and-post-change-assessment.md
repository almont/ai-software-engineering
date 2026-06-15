# Require Project Overview Guidance And Post-Change Assessment

## Status

Accepted

## Date

2026-06-15

## Context

The repository already instructs agents to inspect project structure and read `docs/project-overview.md` when present. It also expects tests after implementation and includes security and reliability guidance.

Two gaps remained for new target projects:

- If `docs/project-overview.md` is missing, agents did not have explicit guidance to propose creating one.
- Post-change verification did not explicitly combine tests with a security and reliability assessment.

## Decision

Update agent instructions, templates, planning presets, implementation presets, README, usage documentation, and project overview to state that agents should inspect the project and suggest creating `docs/project-overview.md` when it is missing.

Also state that after code changes or implementation, agents should run applicable tests or validation checks and perform a brief security and reliability assessment.

## Consequences

This improves onboarding and makes implementation completion more rigorous across projects.

The trade-off is a little more process after small changes. Agents should keep the assessment brief and scale the depth of testing and review to the risk of the change.

## Follow-Up

If teams find the post-change assessment too vague, add a short checklist preset for security and reliability self-review.
