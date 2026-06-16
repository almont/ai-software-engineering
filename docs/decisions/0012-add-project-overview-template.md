# 0012: Add Project Overview Template

## Status

Accepted

## Date

2026-06-16

## Context

The repository instructs agents to read `docs/project-overview.md` when present and to suggest creating one when it is missing. The repository had an existing project overview and guidance for keeping it current, but it did not include a copy-ready template for teams creating a new overview in target repositories.

Human onboarding also needs more than a technical inventory. New contributors benefit from a practical map of purpose, domains, services, common tasks, local development, workflows, operations, tests, and navigation hints.

## Decision

Add `templates/project-overview.md` as an onboarding-first project overview template for humans and AI agents.

The template includes explicit sections for domains and services so teams can map business capabilities, relevant modules, data ownership, external dependencies, workflows, and operational risks without listing every implementation detail. It also includes Mermaid templates for a system context map and critical workflow sequence diagram.

Update README, usage documentation, and the current project overview so the template is discoverable during new project setup and documentation governance.

## Consequences

New repositories have a clearer starting point for `docs/project-overview.md`.

This adds a small amount of documentation surface area, but it reduces ambiguity for onboarding, review, incident investigation, and agent orientation.

## Follow-Up

Keep the template aligned with future changes to agent guidance, maintenance practices, and documentation governance.
