
# Merv's Second Brain

## Quick Capture

- [[00 - Inbox/Inbox|Open Inbox]]
- [[08 - Journal/Journal|Open Journal]]
- [[02 - Projects/Projects|View Projects]]
- [[06 - SOPs/SOPs|View SOPs]]
- [[07 - AI/AI Hub|Open AI Hub]]

## Current Focus

- Build my professional Second Brain
- Improve AI automation skills
- Document n8n workflows
- Build software and automation projects

## Active Projects

```dataview
TABLE status AS Status, priority AS Priority, updated AS Updated
FROM "02 - Projects"
WHERE type = "project" AND status = "active"
SORT priority ASC
```

## Planned Projects

```dataview
TABLE phase AS Phase, owner AS Owner, updated AS Updated
FROM "02 - Projects"
WHERE type = "project" AND status = "planned"
SORT updated DESC
```

## Blocked Projects

```dataview
TABLE phase AS Phase, owner AS Owner, updated AS Updated
FROM "02 - Projects"
WHERE type = "project" AND status = "blocked"
SORT updated DESC
```

## Demo-Complete, Not Production-Ready

```dataview
TABLE phase AS Phase, owner AS Owner, updated AS Updated
FROM "02 - Projects"
WHERE type = "project-checklist"
AND status = "demo-complete"
AND production_ready = false
SORT updated DESC
```

## Project Next Actions

- [[02 - Projects/Obsidian Second Brain/Obsidian Second Brain Setup#Next Action|Obsidian Second Brain — complete the approved optimization phases and final vault audit]]
- [[02 - Projects/Automation/Lead Qualification Practice/Automation Project Checklist#Next Action|Lead Qualification Practice — decide whether to archive the demo or continue with v0.2]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Automation Project Checklist#Next Action|MCP Customer Request Classifier — decide whether to archive the demo or continue with a future version]]

## Recently Updated Project Evidence

```dataview
TABLE type AS Type, status AS Status, updated AS Updated
FROM "02 - Projects"
WHERE contains(["project-checklist", "test-results", "case-study"], type)
AND updated
SORT updated DESC
LIMIT 8
```

## Open Tasks

Detailed lifecycle checklists are excluded. Project-level work is shown under Project Next Actions and Blocked Projects.

```tasks
not done
path does not include Templates/
path does not include 09 - Archive/
filename does not include Automation Project Checklist.md
sort by due
```

## Inbox Notes

```dataview
LIST
FROM "00 - Inbox"
WHERE file.name != "Inbox"
SORT file.mtime DESC
```

## Recently Updated

```dataview
TABLE file.mtime AS "Last Updated"
FROM ""
WHERE !contains(file.path, ".obsidian")
AND !contains(file.path, "Templates")
AND file.name != "Home"
SORT file.mtime DESC
LIMIT 10
```

## Recent Daily Notes

```dataview
LIST
FROM "08 - Journal"
WHERE type = "daily"
SORT date DESC
LIMIT 7
```

## Knowledge Base

- [[04 - Knowledge/Knowledge|Knowledge Hub]]
- [[05 - Resources/Resources|Resources]]
- [[06 - SOPs/SOPs|Standard Operating Procedures]]
- [[07 - AI/AI Hub|AI Knowledge and Prompts]]

## Start a Project

- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
- [[Templates/Client Automation/Client Automation Project|Client Automation Project]]
- [[02 - Projects/Projects|Projects]]
- [[03 - Areas/Automation Operations/Automation Operations|Automation Operations]]
