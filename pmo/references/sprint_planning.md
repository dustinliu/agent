# Sprint Planning Guide

## Overview

This guide provides best practices for bi-weekly sprint planning, helping prioritize and scope work effectively for Production Engineering, DBA, and Software Security teams.

## Pre-Planning Preparation

### Data to Review (1-2 days before planning)

**From Jira:**
- Current sprint completion status
- Carryover stories and blocked items
- Epic progress and burn-down trends
- High-priority bugs and incidents

**From Team:**
- Engineer availability (PTO, on-call schedules)
- Technical debt or maintenance work needed
- Dependencies from other teams

**From Stakeholders:**
- New urgent requests or shifting priorities
- Upcoming deadlines or milestones
- Risk items requiring attention

## Sprint Capacity Calculation

### Base Capacity Formula

```
Team Capacity = (Available Engineers × Sprint Days × Hours per Day) × Focus Factor
```

**Typical focus factors:**
- 70-80%: Teams with stable processes, minimal interruptions
- 60-70%: Teams with on-call rotation, regular maintenance work
- 50-60%: Teams with high interrupt-driven work or many dependencies

### Capacity Adjustments

**Reduce capacity for:**
- Engineers on-call (reduce by 30-50%)
- Planned time off or holidays
- Known meetings/trainings
- Major incident recovery work

**Reserve buffer for:**
- Unplanned work (10-20% of capacity)
- Technical debt/maintenance (10-15% of capacity)
- Code reviews and pair programming

## Work Prioritization Framework

### Priority Tiers

**P0 - Critical (Must Have):**
- Production incidents and critical bugs
- Security vulnerabilities (Critical/High severity)
- Compliance blockers
- Hard deadline commitments

**P1 - High (Should Have):**
- Committed epic work in progress
- Important bugs affecting users
- Dependencies for other teams
- Risk mitigation tasks

**P2 - Medium (Nice to Have):**
- New feature work
- Non-blocking improvements
- Technical debt reduction
- Process improvements

**P3 - Low (Future):**
- Exploratory work
- Nice-to-have enhancements
- Long-term optimization

### Selection Criteria

When choosing stories for the sprint, consider:

1. **Business Value**: Impact on users, stakeholders, or business goals
2. **Risk Reduction**: Addresses identified project risks
3. **Dependencies**: Unblocks other teams or future work
4. **Technical Health**: Reduces technical debt or improves maintainability
5. **Team Growth**: Provides learning opportunities

## Sprint Planning Recommendations

### Analyze Current State

**Epic Progress:**
- Which epics are near completion? (prioritize finishing over starting new)
- Which epics are blocked? (resolve blockers or deprioritize)
- Which epics have high carryover rates? (may need rescoping)

**Team Velocity:**
- What was the team's velocity last 2-3 sprints?
- Are there patterns in completed vs. planned work?
- What caused incomplete work? (rescope, blockers, interrupts)

**Upcoming Risks:**
- Review RAID log for risks requiring mitigation this sprint
- Identify potential blockers for planned work
- Check for upcoming critical dependencies

### Work Distribution Strategy

**Balanced Sprint Composition:**
- 60-70%: Planned epic/feature work
- 15-20%: Bug fixes and technical debt
- 10-15%: Buffer for unplanned work
- 5-10%: Team improvement (tooling, process)

**Engineer Assignment:**
- Balance workload across team members
- Consider skill development opportunities
- Pair complex work with experienced engineers
- Avoid single points of failure (knowledge sharing)

### Story Readiness Check

Before committing to stories, verify:

**Clear Acceptance Criteria:**
- Well-defined "done" conditions
- Testable outcomes
- Performance/security requirements specified

**No Critical Blockers:**
- Required dependencies available
- Access to necessary environments/tools
- Design decisions finalized

**Appropriately Sized:**
- Stories completable within sprint (ideally 1-3 days)
- Large stories broken down into smaller tasks
- Uncertainty addressed or spike work planned

## Sprint Goal Definition

Each sprint should have a clear, concise goal:

**Good sprint goal examples:**
- "Complete user authentication epic and reduce critical security vulnerabilities to zero"
- "Improve database query performance by 30% and migrate legacy backup system"
- "Ship container orchestration MVP and resolve top 5 customer-reported bugs"

**Goal characteristics:**
- Aligned with project objectives
- Measurable and achievable
- Communicates value to stakeholders
- Motivating for the team

## Team-Specific Considerations

### Production Engineering (DevOps/SRE)

**Balance:**
- Feature work vs. operational toil reduction
- Proactive infrastructure work vs. reactive incident response
- Automation investments vs. manual processes

**Plan for:**
- On-call rotation coverage
- Maintenance windows for deployments
- Runbook and documentation updates

### DBA Team

**Balance:**
- Performance optimization vs. new schema changes
- Data migrations vs. BAU support
- Capacity planning vs. immediate requests

**Plan for:**
- Database maintenance windows
- Query optimization investigations
- Backup/restore testing

### Software Security Team

**Balance:**
- Vulnerability remediation vs. proactive security improvements
- Security reviews vs. tool/process development
- Compliance work vs. engineering enablement

**Plan for:**
- Security review requests from other teams
- Incident response readiness
- Security training or awareness activities

## Common Anti-Patterns to Avoid

❌ **Overcommitment**: Planning at 100% capacity leaves no buffer for reality
❌ **Starting too many epics**: Leads to context switching and nothing finishing
❌ **Ignoring technical debt**: Creates long-term velocity drag
❌ **No clear priorities**: Team doesn't know what matters most
❌ **Ignoring blockers**: Carrying blocked stories forward without resolution plans
❌ **Skipping retrospective actions**: Not improving based on past learnings

## Post-Planning Actions

After planning session:

1. **Update Jira**: Move selected stories to sprint, set story points
2. **Communicate**: Share sprint goal and key commitments with stakeholders
3. **Identify risks early**: Flag dependencies or potential blockers to track
4. **Set up checkpoints**: Schedule mid-sprint check-in if needed for high-risk work
