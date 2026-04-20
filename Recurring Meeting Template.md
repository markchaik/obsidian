---
type: recurring_meeting
company:
aliases:
date_created: <% tp.date.now("YYYY-MM-DD") %>
template_name: recurring_meeting
template_version: 0.1
note_subtype:
source:
topics:
related_notes:
tags:
  - 
---
# [[ REC_MTG <% tp.file.title %>]]

tags:
links: 
key stakeholders: 
status: #status/active

---

## Recurring Meeting Overview:
Overview description of this meeting

## Key Resources
Insert links to recurring meeting resources 

## Meeting Instances

```dataview
TABLE file.cday as Created, type as "Type", summary as "Summary"  
FROM [[]]
WHERE file.frontmatter.type = "meeting" 
SORT file.cday DESC
```
