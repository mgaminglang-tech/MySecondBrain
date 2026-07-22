
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

## Open Tasks

```tasks
not done
path does not include Templates
path does not include Archive
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
