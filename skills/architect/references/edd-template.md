# EDD Template (Engineering Design Document)

## Document Header

```markdown
# EDD: [Feature/System Name]

**Author:** [Name]
**Status:** Draft | In Review | Approved | Implemented
**Created:** YYYY-MM-DD
**Last Updated:** YYYY-MM-DD
**Reviewers:** [Names]
```

## Required Sections

### 1. Overview

Brief summary (2-3 sentences) of what this document proposes.

### 2. Problem Statement

- What problem are we solving?
- Who is affected?
- What is the current state?

### 3. Goals and Non-Goals

**Goals:**
- Specific, measurable objectives
- What success looks like

**Non-Goals:**
- Explicitly out of scope items
- Prevents scope creep

### 4. Background

- Relevant context
- Prior art or existing solutions
- Why now?

### 5. Proposed Solution

#### 5.1 High-Level Architecture

- System diagram (Mermaid)
- Component interactions
- Data flow

#### 5.2 API Design

For each endpoint:
```
[METHOD] /api/v1/resource
Request:  { field: type }
Response: { field: type }
Errors:   [400, 401, 404, 500]
```

#### 5.3 Database Schema

- Table definitions with types
- Indexes
- Relationships (FK)
- Migration strategy

#### 5.4 Key Technical Decisions

| Decision | Options Considered | Choice | Rationale |
|----------|-------------------|--------|-----------|
| ...      | ...               | ...    | ...       |

### 6. Implementation Plan

Phased approach with dependencies:

| Phase | Tasks | Dependencies | Deliverables |
|-------|-------|--------------|--------------|
| 1     | ...   | None         | ...          |
| 2     | ...   | Phase 1      | ...          |

### 7. Testing Strategy

- Unit tests
- Integration tests
- Load/Performance tests
- Manual QA scenarios

### 8. Rollout Plan

- Feature flags
- Gradual rollout percentage
- Rollback procedure
- Monitoring/Alerts

### 9. Security Considerations

- Authentication/Authorization
- Data encryption
- Input validation
- OWASP top 10 review

### 10. Open Questions

| Question | Owner | Status | Resolution |
|----------|-------|--------|------------|
| ...      | ...   | Open   | ...        |

### 11. References

- Related documents
- External resources
- Prior EDDs
