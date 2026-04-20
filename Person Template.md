<%*  
const modalForm = app.plugins.plugins.modalforms.api;  
const result = await modalForm.openForm("Person");
_%>
---
tags:
  - 
type: person
note_subtype:
aliases:
source:
description:
topics:
related_notes:
person_given_name: <% result.get("given_name") %>
person_surname:  <% result.get("surname") %>
person_nicknames:
person_company: <% result.get("company") %>
person_title: <% result.get("title") %>
person_phone:
person_email:
person_website:
person_city:
person_state:
person_country:
person_previous_companies:
person_birthday: <% result.get("birthday") %>
person_languages:
person_date_last_spoken:
person_follow_up:
date_created:  <% tp.date.now("YYYY-MM-DD") %>
template_name: person
template_version: 0.3
---

# [[<% tp.file.title %>]]
<% await tp.file.move("/05 Dayframe/CRM/People/" + tp.file.title) %>

## Notes:


## Meetings:

![[Meetings.base#By Attendee]]

```dataview
TABLE file.frontmatter.date_meeting as "Meeting Date", summary AS "Summary" 
FROM [[]]
WHERE type = "meeting"
SORT file.cday DESC
```

## Other Notes:
```dataview
TABLE file.frontmatter.type as Type, dateformat(file.cday,"yyyy-MM-dd") as "Created Date", summary AS "Summary" 
FROM [[]]
WHERE type != "meeting"
SORT file.cday DESC
```