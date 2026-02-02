---
name: daily-planner
description: Generate daily work reports and manage daily planning. Integrates with Things MCP (todos), Jira MCP (tickets), and Obsidian MCP (documents). Use when the user asks to plan their day, generate a work report, check today's tasks, or review open tickets. Triggers include phrases like "plan my day", "what's on my plate today", "daily report", "today's tasks", or "my open tickets".
---

# Daily Planner

Create comprehensive daily plans in structured note format, suitable for tools like Obsidian or Notion.

## Task Management

All todos are managed through **Things MCP**. Use Things MCP tools to:

- Retrieve existing tasks
- Always create new tasks to Inbox
- Update task status
- Organize by projects and areas (`get_projects`, `get_areas`)

## Ticket Management

All tickets are managed through **Jira**. Use Jira MCP tools to:

- Search and retrieve issues
- Create new tickets
- Update ticket status and transitions
- Add comments and worklogs



## Document Management

All documents are managed through **Obsidian**. Use Obsidian MCP tools to:

- Search and retrieve notes
- Create and append content to notes
- Manage daily/periodic notes
- Organize files within the vault

### Daily Note

- **Path pattern**: `DailyNote/YYYY/MM/YYYY-MM-DD.md`
- **Get today's note**: Use `mcp__mcp-obsidian__obsidian_get_periodic_note` with `period: "daily"`

### Project Documents

- **Path pattern**: `Work/Projects/[ProjectName].md`
- **Template**: `assets/project.md`

#### Template Properties

| Property | Description | Example |
|----------|-------------|---------|
| `jira` | Jira ticket key | `proj-123` |
| `space` | Jira project identifier | `TWPE` or `TWECP` |
| `created` | Document creation date | `2025-01-15` |
| `updated` | Last update date | `2025-01-20` |

## Jobs

### Generate Daily Work Report

Collect and summarize today's work items from three sources:

1. **Today's To-Do List** - Use `mcp__things__get_today` to retrieve tasks due today
2. **My Open Jira Tickets** - Use `mcp__atlassian__searchJiraIssuesUsingJql` with JQL: `assignee = currentUser() AND statusCategory not in (Done) ORDER BY updated DESC`, fields: `["summary","status","issuetype","priority","created","updated","duedate","project"]`, maxResults: `50`
3. **Daily Note** - Use `mcp__mcp-obsidian__obsidian_get_periodic_note` with `period: "daily"` to retrieve today's note content

#### Output Template

```markdown
# Daily Report - {date}

## Today's Tasks
| Task | Note | Project/Area |
|------|--------|---------|
| title | summary of note | Project or Area|

## Jira Tickets
| Key | Summary | Project | 
|-----|---------|--------|
| {ticket data} |

## Notes
{summary content from daily note, if available}
```
