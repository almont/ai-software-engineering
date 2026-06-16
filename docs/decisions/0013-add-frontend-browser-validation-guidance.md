# 0013: Add Frontend Browser Validation Guidance

## Status

Accepted

## Date

2026-06-16

## Context

The repository already requires agents to run applicable tests or validation checks after code changes and to perform a brief security and reliability assessment. Frontend changes can pass unit tests, lint, typecheck, or build checks while still breaking user flows, visual layout, responsive behavior, routing, forms, authentication, checkout, or onboarding.

The guidance needed to make browser-based validation explicit without requiring heavyweight end-to-end automation for every small frontend change.

## Decision

Add risk-calibrated frontend validation guidance to canonical agent instructions, project templates, implementation guidance, change-risk calibration, post-change assessment, usage documentation, the current project overview, and the frontend example.

For frontend changes that affect user flows, routing, forms, visual layout, responsiveness, authentication, checkout, onboarding, or other UI behavior, agents should include browser-based validation. When the project already uses Playwright, Cypress, or another end-to-end framework, agents should run related tests for affected flows when practical. If browser automation is unavailable, agents should perform a manual browser smoke test or explain why browser validation was not practical.

## Consequences

Frontend validation expectations become clearer and more likely to catch user-visible regressions.

The guidance remains calibrated by risk and project capability, avoiding a blanket requirement to run Playwright or equivalent tooling for every frontend change.

## Follow-Up

Keep frontend validation guidance aligned with future changes to post-change assessment, frontend examples, and change-risk calibration guidance.
