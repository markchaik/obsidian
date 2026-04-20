---
type: dailynote
template_name: daily-note
template_version: 0.3
date_created: <% tp.date.now("YYYY-MM-DD") %>
date_dailynote: <% moment(tp.file.title,'YYYY-MM-DD').format("YYYY-MM-DD") %>
note_subtype:
aliases:
source:
topics:
related_notes:
tags:
  -
---

# <% moment(tp.file.title,'YYYY-MM-DD').format("dddd, MMMM DD, YYYY") %>

## Agenda:

## Priorities:

## Notes:



## Today's Meetings:
```dataview
TABLE file.frontmatter.date_meeting as "Meeting Date", summary AS "Summary", dateformat(file.cday,"yyyy-MM-dd") as Created where type = "meeting" and file.frontmatter.date_meeting = this.file.frontmatter.date_dailynote
SORT file.cday DESC
```

## Notes Created Today :

```dataview 
Table file.frontmatter.type as Type, dateformat(file.cday,"yyyy-MM-dd") as Created, dateformat(file.mday,"yyyy-MM-dd") as Modified WHERE file.cday = date(this.file.frontmatter.date_dailynote)
SORT file.ctime asc
```

## Notes Last Edited Today :
```dataview 
Table file.frontmatter.type as Type, dateformat(file.cday,"yyyy-MM-dd") as Created, dateformat(file.mday,"yyyy-MM-dd") as Modified WHERE file.cday = date(this.file.frontmatter.date_dailynote)
SORT file.mtime asc
```
