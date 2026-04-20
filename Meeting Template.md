<%*  
const modalForm = app.plugins.plugins.modalforms.api;  
const defaultValues = { 
    meetingDate: tp.date.now("YYYY-MM-DD"), // Add default value using Templater's date helper
};
const result = await modalForm.openForm("Meeting", { values: defaultValues });
const attendeeLinks = result.getData().attendees?.length ? result.getData().attendees.map(p => `\n - "[[${p}]]"`).join('') : '';
const companyLinks = result.getData().companies?.length ? result.getData().companies.map(p => `\n - "[[${p}]]"`).join('') : '';
const projectLinks = result.getData().projects?.length ? result.getData().projects.map(p => `\n - "[[${p}]]"`).join('') : '';
const recurringLinks = result.getData().recurring_meeting?.length ? result.getData().recurring_meeting.map(p => `\n - "[[${p}]]"`).join('') : '';
_%>
---
tags:
  - 
type: meeting
subtype:
aliases:
source:
description:
topics:
related_notes:
meeting_recurring_parent: <% recurringLinks %> 
meeting_date: <% result.get("meetingDate") %>
meeting_attendees:  <% attendeeLinks %> 
meeting_project: <% projectLinks %> 
meeting_company: <% companyLinks %> 
meeting_summary:
date_created: <% tp.date.now("YYYY-MM-DD") %>
template_name: meeting
template_version: 0.3
---

# [[<% tp.date.now("YYYY-MM-DD") + " " + tp.file.title %>]]

## Agenda:


## Notes:


## Summary and Next Steps:


## Links:
Daily Note: [[<% "/05 Dayframe/Daily Notes/" + tp.date.now("YYYY") + "/" + tp.date.now("MM") + "/" + tp.date.now("YYYY-MM-DD") %>]]

<% await tp.file.move("/05 Dayframe/Meetings/" + tp.date.now("YYYY-MM-DD") + " " + tp.file.title) %>



