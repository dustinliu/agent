# User Story Guide

## Standard Format

```
As a [user type],
I want to [action/goal],
So that [benefit/value].
```

## Complete User Story Template

```markdown
## [US-XXX] [Brief Title]

### Story
As a [user type],
I want to [action/goal],
So that [benefit/value].

### Acceptance Criteria
- [ ] Given [context], when [action], then [expected result]
- [ ] Given [context], when [action], then [expected result]

### Priority
[P0/P1/P2]

### Notes
[additional context]
```

## INVEST Criteria

Good user stories should be:

| Criteria | Description |
|----------|-------------|
| **I**ndependent | Can be developed without depending on other stories |
| **N**egotiable | Details can be discussed and refined |
| **V**aluable | Delivers value to the user |
| **E**stimable | Team can estimate the effort |
| **S**mall | Can be completed in one sprint |
| **T**estable | Has clear acceptance criteria |

## Acceptance Criteria Format (Given-When-Then)

```
Given [precondition/context]
When [action is performed]
Then [expected outcome]
```

### Example

```
Given I am a logged-in user on the dashboard
When I click the "Export" button
Then a CSV file downloads containing my data
```

## Examples by Type

### Feature Story
```
As a premium user,
I want to export my reports as PDF,
So that I can share them with stakeholders offline.
```

### Bug Fix Story
```
As a user,
I want the search results to load within 2 seconds,
So that I can find information quickly without frustration.
```

### Technical Story
```
As a developer,
I want to migrate the database to PostgreSQL,
So that we can support more concurrent users.
```

## Story Splitting Strategies

When a story is too large, split by:

1. **Workflow steps** - Break down a process into individual steps
2. **Business rules** - One story per rule variation
3. **Data variations** - Different data types or formats
4. **Operations** - CRUD (Create, Read, Update, Delete)
5. **User roles** - Different personas with different needs
6. **Platforms** - Web, mobile, API

## Common Mistakes to Avoid

1. **Too vague** - "As a user, I want a better experience"
2. **Too technical** - "As a user, I want a Redis cache"
3. **Multiple features** - Combining unrelated functionality
4. **Missing value** - Omitting the "so that" clause
5. **Untestable criteria** - "The page should be fast"

## Critical Rule: No Technical Implementation

User stories must describe **user needs**, not **technical solutions**.

### ❌ Bad Examples (Technical)
- "As a user, I want data stored in PostgreSQL so queries are fast"
- "As a user, I want the app to use WebSocket for real-time updates"
- "As a user, I want the API to return JSON with pagination tokens"

### ✅ Good Examples (User-Focused)
- "As a user, I want my searches to return results within 2 seconds"
- "As a user, I want to see new messages appear without refreshing the page"
- "As a user, I want to browse large result sets without long loading times"

### Remember
- **Users don't care about technology** - they care about outcomes
- **Technical stories are for engineering** - not product backlogs
- **Acceptance criteria describe behavior** - not implementation
