# Protect Legacy Project Architecture

## Status

Accepted

## Date

2026-06-15

## Context

The repository already says agents should use DDD only when relevant and should follow existing architecture. In legacy projects, that guidance could still be interpreted too broadly: an agent might introduce DDD layers or new architectural patterns because it found business logic, even when the project does not already use those structures.

## Decision

Add explicit guidance that agents must not introduce DDD layers, new architectural patterns, or structural migrations in legacy projects unless the existing architecture already uses them or the user explicitly requests that migration.

Agents should fit changes into the current structure and list broader architecture improvements as follow-up work when relevant.

## Consequences

This reduces accidental architecture churn in legacy codebases and keeps changes easier to review.

The trade-off is that some implementations may retain imperfect existing structure in the short term. That is intentional unless the user asks for a migration or the architecture change is already part of the accepted scope.

## Follow-Up

If teams frequently modernize legacy applications, consider adding a dedicated architecture migration planning preset.
