---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# Project Routing Standard

## Purpose

Define how humans and AI agents choose one primary home for a new project inside `10 Projects/`.

## Routing Principles

1. **Platform-specific beats generic.** A GoHighLevel CRM belongs in `13 GoHighLevel`, not `12 CRM`.
2. **Primary outcome beats supporting technology.** An AI support agent using n8n belongs in `16 AI Agents`; n8n is a supporting component.
3. **One project has one home.** Never duplicate an initiative across categories. Record secondary components in the Project Hub metadata or component list.
4. **Search before creating.** Update an existing project when it is the same initiative. Create a new project only when it is genuinely separate.
5. **Choose by dominant intent when ambiguous.** Route according to the project's main outcome or dominant platform.

## Approved Categories

### 11 Automation

- n8n workflows
- Make or Zapier automations
- integrations and API workflows
- event-driven business processes

### 12 CRM

- generic CRM systems and architecture
- pipelines
- lead or customer lifecycle projects
- platform-agnostic CRM projects

### 13 GoHighLevel

- any project where GoHighLevel is the primary platform
- GHL CRM, funnels, automations, websites, and client systems

### 14 Funnels

- standalone funnels and conversion journeys
- landing-page sequences
- lead magnets and nurture flows

### 15 Websites

- business websites and redesigns
- landing sites
- website architecture

### 16 AI Agents

- autonomous or semi-autonomous agents
- support, sales, and research agents
- AI orchestration where the agent is the primary product

### 17 Internal Systems

- reusable internal operating systems and SOP systems
- AI OS and project-management systems
- reusable business infrastructure
- internal standards and frameworks

### 18 Experiments

- prototypes, spikes, and proofs of concept
- temporary tests
- ideas not yet promoted into a real project

## Decision Process

Before creating a project:

1. Identify the primary outcome.
2. Identify whether a platform dominates the project.
3. Search for an existing matching project.
4. Choose exactly one category.
5. Create or update the project there.
6. Record secondary technologies and components in the Project Hub.
7. Never duplicate the initiative across categories.

## Examples

| Initiative | Route |
| --- | --- |
| Build a GoHighLevel CRM for a dental clinic | `13 GoHighLevel` |
| Build an n8n workflow syncing Facebook leads to Airtable | `11 Automation` |
| Build an AI support agent using n8n and Slack | `16 AI Agents` |
| Design a platform-agnostic CRM for a real estate team | `12 CRM` |
| Test a webhook architecture | `18 Experiments` |
| Build a reusable client onboarding operating system | `17 Internal Systems` |

## Ambiguity Rule

- If confidence is low, do not scatter files across categories.
- Choose the most likely primary home and record the uncertainty in the Project Hub.
- Ask for clarification only when the routing choice would materially change the project structure.

## Agent Rules

- Apply this standard before creating a project path.
- Search the most likely category and project paths first.
- Expand the search only when no likely match is found.
- Use the Project Hub for secondary technologies, components, and routing uncertainty.
- Never create duplicate homes to avoid making a routing decision.

## Do / Don't

| Do | Don't |
| --- | --- |
| Choose one home by dominant platform or primary outcome. | Duplicate an initiative across categories. |
| Search likely paths before creating anything. | Scan unrelated project folders by default. |
| Record secondary components in the Project Hub. | Route by every tool used in the project. |
| Record low-confidence routing decisions. | Scatter files when routing is ambiguous. |
