---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# Project Naming Standard

## Purpose

Create predictable, readable, and searchable project names for humans and AI agents.

## Core Principles

- Describe the project outcome, not the current task.
- Keep names short but specific.
- Use Title Case.
- Keep one stable project name throughout its lifecycle.
- Avoid vague names such as `Test`, `New Project`, `Automation 1`, `CRM Final`, and `Misc`.
- Avoid dates unless a date is part of the project's identity.
- Avoid `v2` or `v3` in the primary name unless separate versions are actively maintained.
- Avoid implementation tool names unless the tool is central to the project's identity.

## Preferred Naming Patterns

### Client or Business Projects

Pattern: `<Client or Business> - <Primary Outcome>`

Examples:

- `Acme Dental - Lead Management CRM`
- `Northstar Realty - Lead Qualification System`
- `BrightSmile Dental - Appointment Funnel`

### Platform-Specific Projects

Pattern: `<Client or Business> - <Platform> <Primary Outcome>`

Examples:

- `Acme Dental - GoHighLevel CRM`
- `Northstar Realty - GoHighLevel Lead Funnel`

### Internal Projects

Pattern: `<System or Outcome Name>`

Examples:

- `Merv’s AI OS`
- `Client Onboarding System`
- `Automation Testing Framework`

### Experiments

Pattern: `EXP - <Short Experiment Name>`

Examples:

- `EXP - Telegram Intake Prototype`
- `EXP - Gemini Classification Test`

### Portfolio or Demo Projects

Pattern: `<Outcome> - <Industry or Use Case>`

Examples:

- `Lead Qualification CRM - Real Estate`
- `AI Support Agent - Ecommerce`

## Folder Naming Rule

The project folder name must match the approved project name exactly.

Example:

`10 Projects/13 GoHighLevel/Acme Dental - GoHighLevel CRM/`

Do not create:

- duplicate folders with small naming variations
- names containing `final`, `final-final`, `new`, or `latest`
- separate project folders for components of the same project

## Component Rule

A project may contain CRM, automation, funnel, website, and AI components without creating multiple project homes. List those components in the Project Hub instead of encoding them in a long folder name.

## Renaming Rule

Once a project contains meaningful work or links:

- do not rename it casually
- rename only when the current name is materially misleading
- update internal links and references when a rename is approved

## Search Before Creating

Before creating a project:

1. Search for the exact proposed name.
2. Search for near matches and likely synonyms.
3. Prefer updating an existing matching project.
4. Create a new folder only when the initiative is genuinely separate.

## Agent Rules

- Choose a discriminative name that reveals relevance without opening the folder.
- Use the appropriate approved naming pattern.
- Keep unnecessary metadata and component lists out of the folder name.
- Confirm that the exact or a near-matching project does not already exist.
- Preserve the approved name throughout the project lifecycle.

## Do / Don't

| Do | Don't |
| --- | --- |
| Name the stable project outcome. | Name the current task or phase. |
| Use a short, specific Title Case name. | Use vague labels such as `New Project` or `Misc`. |
| Search exact names, near matches, and synonyms first. | Create small naming variations of an existing project. |
| List components in the Project Hub. | Build every component or tool into a long folder name. |
| Rename only with approval when materially misleading. | Add `final`, `latest`, or casual version suffixes. |
