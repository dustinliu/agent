---
name: pmo
description: Project Management Office assistant for planning, tracking, and reporting on technical projects using Scrum methodology with Jira. Use when (1) analyzing project organization and work planning, (2) performing risk assessment and providing mitigation recommendations, (3) generating progress reports showing epic completion status and blockers, (4) providing sprint planning recommendations for upcoming 2-week sprints. Supports Production Engineering (DevOps/SRE), DBA, and Software Security teams.
---

# PMO (Project Management Office)

## Overview

This skill provides comprehensive project management support for technical teams running Scrum with Jira. It helps analyze project health, assess risks, generate progress reports, and provide data-driven recommendations for sprint planning.

## Core Capabilities

The PMO skill supports four primary capabilities:

### 1. Project Organization & Work Planning

Analyze current project state and provide recommendations for organizing and prioritizing upcoming work.

**Use when:**
- Starting a new initiative or project
- Reorganizing work priorities
- Determining how to structure epics and stories
- Balancing multiple team priorities

**Approach:**
1. Review current Jira state (initiatives, epics, stories)
2. Analyze team capacity and velocity trends
3. Assess work distribution and priorities
4. Provide recommendations for work organization

**Key considerations:**
- Team type (PE, DBA, Security) influences priorities
- Balance feature work vs. technical debt vs. operational needs
- Consider dependencies and blockers
- Align work with business objectives

### 2. Risk Assessment & Mitigation

Identify project risks using RAID log methodology and provide mitigation recommendations.

**Use when:**
- Starting a new sprint or initiative
- Project showing signs of delays or issues
- Preparing for stakeholder updates
- Periodic risk reviews (bi-weekly or monthly)

**Approach:**
1. Read [references/risk_management.md](references/risk_management.md) for framework details
2. Analyze Jira data for risk indicators (blocked epics, velocity drops, carryover patterns)
3. Review project documentation (meeting notes, architecture docs)
4. Apply team-specific risk categories (PE, DBA, Security)
5. Generate RAID log using [assets/risk_log_template.md](assets/risk_log_template.md)

**Risk data sources:**
- Jira: blocked/delayed epics, sprint burndown, velocity trends
- Documentation: meeting notes, incident reports, retrospectives
- Team input: capacity constraints, technical challenges

### 3. Progress Reporting

Generate comprehensive progress reports showing epic completion, sprint metrics, and attention items.

**Use when:**
- Regular status updates (weekly/bi-weekly)
- Stakeholder reporting needs
- Sprint review preparation
- Leadership asks for project status

**Report includes:**
1. Completed epics and outcomes
2. In-progress epics with completion percentages
3. Sprint velocity and metrics
4. Critical blockers and risks
5. Team capacity and availability
6. Upcoming focus areas

**Approach:**
1. Query Jira for epic and story status via Jira MCP
2. Calculate completion percentages and velocity trends
3. Identify blockers, risks, and attention items
4. Use [assets/progress_report_template.md](assets/progress_report_template.md)
5. Generate markdown report with clear status indicators

### 4. Sprint Planning Recommendations

Provide data-driven recommendations for upcoming sprint work selection and prioritization.

**Use when:**
- Preparing for bi-weekly sprint planning
- User asks "what should we work on next sprint?"
- Team needs help prioritizing backlog
- Balancing competing priorities

**Approach:**
1. Read [references/sprint_planning.md](references/sprint_planning.md) for best practices
2. Analyze current sprint completion and carryover
3. Review epic progress and priorities
4. Calculate team capacity for upcoming sprint
5. Recommend story selection based on:
   - Epic completion opportunities (finish in-progress work)
   - Priority and business value
   - Risk mitigation needs
   - Team capacity and velocity
   - Dependencies and blockers

**Recommendations include:**
- Prioritized list of epics/stories for next sprint
- Capacity allocation strategy
- Risks to address
- Dependencies to monitor

## Jira Integration

This skill interacts with Jira through the Jira MCP tool for:

**Query operations:**
- Fetching initiative, epic, and story details
- Getting sprint progress and burndown data
- Listing blocked or at-risk items
- Calculating epic completion percentages
- Analyzing velocity trends

**Note:** PMO skill reads and analyzes Jira data but does not create or modify Jira items.

**Jira hierarchy:** Refer to [references/jira_workflow.md](references/jira_workflow.md) for details on:
- Project → Initiative → Epic → Story structure
- Story lifecycle states
- Epic progress tracking
- Scrum workflow (2-week sprints)

## Working with Multiple Teams

This skill supports three team types with different characteristics:

**Production Engineering (DevOps/SRE):**
- Balance feature work vs. operational toil reduction
- Account for on-call rotation impact on capacity
- Consider infrastructure maintenance needs
- Prioritize automation investments

**DBA Team:**
- Balance performance optimization vs. new schema work
- Plan for database maintenance windows
- Consider query optimization investigations
- Account for BAU support requests

**Software Security Team:**
- Balance vulnerability remediation vs. proactive improvements
- Account for security review requests from other teams
- Consider compliance work requirements
- Plan for incident response readiness

When providing recommendations, tailor advice to the specific team's priorities and constraints.

## Resources

### references/

**[risk_management.md](references/risk_management.md)** - Comprehensive risk assessment framework
- RAID log methodology (Risks, Assumptions, Issues, Dependencies)
- Risk matrix (Impact × Probability)
- Team-specific risk categories for PE, DBA, and Security
- Mitigation strategy templates
- Read this when performing risk assessments

**[sprint_planning.md](references/sprint_planning.md)** - Sprint planning best practices
- Pre-planning preparation checklist
- Capacity calculation formulas
- Work prioritization framework
- Sprint goal definition guidance
- Team-specific planning considerations
- Read this when providing sprint planning recommendations

**[jira_workflow.md](references/jira_workflow.md)** - Jira structure and workflow
- Hierarchy explanation (Project → Initiative → Epic → Story)
- Scrum workflow and story lifecycle
- Epic progress tracking methods
- Best practices for PM and engineers
- Read this for Jira context and terminology

### assets/

**[progress_report_template.md](assets/progress_report_template.md)** - Progress report template
- Comprehensive report structure
- Epic progress tables
- Sprint metrics section
- Attention items (blockers, risks, dependencies)
- Use this template when generating progress reports

**[risk_log_template.md](assets/risk_log_template.md)** - RAID log template
- Structured RAID log format
- Risk matrix visualization
- Tracking tables for all RAID categories
- Status indicators and priority levels
- Use this template when generating risk assessments

## Workflow Examples

**Example 1: User asks for project organization help**

User: "Help me organize and plan the work for my Software Security team"

Actions:
1. Query Jira for current initiatives, epics, and stories
2. Analyze epic progress and story distribution
3. Review team capacity and recent velocity
4. Provide recommendations for work prioritization
5. Suggest epic organization and story breakdown if needed

**Example 2: User requests risk assessment**

User: "Assess risks for our current DBA projects"

Actions:
1. Read [references/risk_management.md](references/risk_management.md)
2. Query Jira for blocked items, velocity trends, carryover patterns
3. Request access to relevant documentation (meeting notes, incident reports)
4. Apply DBA-specific risk categories
5. Generate RAID log using [assets/risk_log_template.md](assets/risk_log_template.md)
6. Provide mitigation recommendations

**Example 3: User needs progress report**

User: "Generate a progress report for Production Engineering"

Actions:
1. Query Jira for epic completion status and sprint metrics
2. Identify completed vs. in-progress vs. upcoming epics
3. Calculate completion percentages and velocity trends
4. Identify blockers, risks, and attention items
5. Use [assets/progress_report_template.md](assets/progress_report_template.md)
6. Generate comprehensive markdown report

**Example 4: User asks for sprint planning recommendations**

User: "What should we work on in the next sprint?"

Actions:
1. Read [references/sprint_planning.md](references/sprint_planning.md)
2. Query Jira for current sprint status and backlog
3. Calculate team capacity for next sprint
4. Analyze epic priorities and completion opportunities
5. Review risks that need mitigation
6. Provide prioritized recommendations with rationale

## Best Practices

**When analyzing projects:**
- Always query Jira first to understand current state
- Consider team-specific constraints and priorities
- Look for patterns in velocity, carryover, and blockers
- Base recommendations on data, not assumptions

**When assessing risks:**
- Use RAID log framework consistently
- Prioritize using risk matrix (probability × impact)
- Provide actionable mitigation plans
- Track risks over time to measure trends

**When generating reports:**
- Use clear status indicators (🟢⚠️🔴)
- Include both quantitative metrics and qualitative insights
- Highlight attention items prominently
- Keep reports concise and scannable

**When recommending work:**
- Prioritize finishing in-progress epics over starting new ones
- Balance capacity across work types (features, bugs, tech debt)
- Consider dependencies and blockers
- Align recommendations with team and business goals
