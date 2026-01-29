# Jira Workflow and Hierarchy

## Jira Hierarchy Structure

```
Project (專案)
  └── Initiative (計畫)
        └── Epic (目標)
              └── Story (任務)
                    └── Sub-task (子任務) [Optional]
```

### Project (專案)
Top-level organizational unit representing a major body of work or team.

**Characteristics:**
- Typically maps to a team or major program
- Contains one or more initiatives
- Has its own board, backlog, and workflow

**Examples:**
- "Production Engineering Q1 2024"
- "DBA Team Infrastructure"
- "Software Security Program"

### Initiative (計畫)
Strategic effort or program of work within a project.

**Characteristics:**
- Represents a significant business objective or outcome
- Groups related epics together
- Typically spans multiple sprints or quarters
- One initiative per project for focused execution

**Examples:**
- "Kubernetes Migration Initiative"
- "Database Performance Optimization Program"
- "Zero Trust Security Implementation"

**Relationship:** 1 Project : 1 Initiative

### Epic (目標)
Specific, measurable goal that delivers value toward the initiative.

**Characteristics:**
- Created and owned by PM/PMO
- Represents what you want to achieve
- Broken down into stories by engineers
- Tracked for completion percentage and progress
- Typically completable within 1-3 sprints

**Good epic examples:**
- "Implement automated database backup rotation"
- "Deploy production monitoring dashboard"
- "Complete API security audit and remediation"

**Poor epic examples (too vague):**
- "Improve performance"
- "Fix bugs"
- "Update infrastructure"

**Relationship:** 1 Initiative : Multiple Epics

### Story (任務)
Specific piece of work that contributes to completing an epic.

**Characteristics:**
- Created by engineers (not PM/PMO)
- Describes how to achieve the epic's goal
- Independently deliverable and testable
- Completable within a single sprint (ideally 1-3 days)
- Assigned to individual engineers

**Story format:**
```
As a [role]
I want [capability]
So that [benefit]

Acceptance Criteria:
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3
```

**Examples:**
- "Set up S3 bucket for backup storage with lifecycle policies"
- "Implement backup validation script"
- "Configure automated backup scheduling in cron"

**Relationship:** 1 Epic : Multiple Stories

### Sub-task (子任務) [Optional]
Breakdown of story into smaller technical steps.

**When to use:**
- Story is complex and needs decomposition
- Multiple engineers working on same story
- Tracking granular progress is valuable

**Avoid overuse:**
- Don't create sub-tasks for simple stories
- Sub-tasks should not span multiple days
- If sub-tasks feel like stories, rescope the parent story

## Scrum Workflow

### Sprint Cycle (2 weeks)

**Week 1:**
- Day 1: Sprint Planning
- Day 2-5: Development work
- Daily: Stand-up meetings

**Week 2:**
- Day 6-9: Development work
- Day 10 AM: Sprint Review
- Day 10 PM: Sprint Retrospective
- Continuous: Sprint Planning preparation

### Story Lifecycle States

**Standard workflow:**
```
To Do → In Progress → Code Review → Testing → Done
```

**State definitions:**

**To Do:**
- Story is ready to be worked on
- Acceptance criteria defined
- No blockers

**In Progress:**
- Engineer actively working on the story
- Updates added to story comments/description
- Blockers flagged immediately

**Code Review:**
- PR created and linked to story
- Awaiting peer review
- Addressing review feedback

**Testing:**
- Code merged to test environment
- QA validation or acceptance testing
- Bug fixes if needed

**Done:**
- Acceptance criteria met
- Code merged to main/production
- Documentation updated if needed

### Epic Progress Tracking

**Epic status indicators:**
- **Not Started**: No stories in progress
- **In Progress**: At least one story in progress
- **At Risk**: Behind schedule or blocked
- **Completed**: All stories done

**Epic completion calculation:**
```
Completion % = (Done Stories / Total Stories) × 100
```

**Health signals:**
- ✅ Green: On track, ≥80% of planned stories completed by sprint end
- ⚠️ Yellow: At risk, 50-79% completion with 1-2 sprints remaining
- 🔴 Red: Blocked or delayed, <50% completion with <1 sprint remaining

## Best Practices

### For PM/PMO (Epic Creation)

**Do:**
- Define clear, measurable epic goals
- Align epics with initiative objectives
- Set realistic timelines based on team capacity
- Review epic progress weekly

**Don't:**
- Create epics that are too broad ("Improve system")
- Micromanage how engineers break down work
- Change epic scope mid-sprint without discussion
- Create dependencies between too many epics

### For Engineers (Story Creation)

**Do:**
- Break epics into right-sized stories (1-3 days)
- Write clear acceptance criteria
- Flag blockers or dependencies immediately
- Update story status daily

**Don't:**
- Create stories that are too large (>5 days)
- Start work before story is defined
- Leave stories in limbo without updates
- Hide problems or delays

### For Team (Sprint Execution)

**Do:**
- Limit work in progress (WIP)
- Focus on completing stories before starting new ones
- Communicate blockers early
- Update Jira status promptly

**Don't:**
- Start too many stories simultaneously
- Let stories stay in "In Progress" for >3 days without updates
- Work on unplanned items without discussion
- Carry over >20% of stories to next sprint repeatedly

## Jira Interactions via MCP

The PMO skill interacts with Jira through the Jira MCP tool. Common operations:

**Query operations:**
- Fetch initiative/epic/story details
- Get sprint progress and burndown
- List blocked or overdue items
- Calculate epic completion percentages

**Analysis operations:**
- Identify at-risk epics
- Track velocity trends
- Find blockers and dependencies
- Generate progress reports

**Note:** PMO skill does not create or modify Jira items—only reads and analyzes data.
