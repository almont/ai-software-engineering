# 0014: Rename Ambiguity Resolution Preset

## Status

Accepted

## Date

2026-06-16

## Context

The ambiguity-resolution workflow was originally named with informal language. The behavior is useful, but the file name should communicate the preset's purpose clearly in repository navigation, onboarding, and project setup.

## Decision

Rename the preset to `presets/ambiguity-resolution.md`.

Update canonical agent instructions, project templates, README, usage documentation, project overview, and decision log wording to use the clearer name.

## Consequences

The preset name now describes the capability directly, which makes it easier to discover and understand.

Existing consumers that referenced the previous file name need to update their links or copied instructions.

## Follow-Up

Keep future references aligned on `presets/ambiguity-resolution.md`.
