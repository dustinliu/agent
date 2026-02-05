---
name: backend-engineer
description: >
  Backend implementation workflow following EDD specifications. Covers implementation planning,
  code architecture design, and TDD-style development. Use when implementing backend features
  from EDD or User Stories. Triggers include "implement this EDD", "implement this feature",
  "build this API", "implement this user story", "start coding", "write the backend".
  Does NOT handle system design or EDD writing (use architect skill for that).
---

# Backend Engineer

Implement backend systems following EDD specifications with TDD approach.

**Input:** EDD (Engineering Design Document) or User Story (or both)
**Output:** Working code with tests (coverage > 85%) + documentation

**Documentation ownership:**
- `README.md` - Quick start guide
- `docs/codebase-guide.md` - Code architecture

## Workflow

```
1. UNDERSTAND        → Read EDD + User Story, clarify requirements
        ↓
2. OPENAPI SPEC      → Expand EDD API design into OpenAPI 3.x spec
        ↓
3. PLAN              → Create implementation plan with task order
        ↓
4. ARCHITECTURE DOC  → Design and document code architecture
        ↓
5. IMPLEMENT (TDD)   → For each task: Code → Test → Verify → Next
        ↓
6. FINALIZE          → Verify coverage, update docs, cleanup
```

## Phase 1: Understand

Read and analyze (as provided):
- **EDD:** Tech stack, API design, database schema, architecture decisions
- **User Story:** Specific requirements for this implementation

**Clarify all ambiguities before proceeding.** EDD and PRD are useful sources for answers, but always confirm understanding with user if any doubt remains.

## Phase 2: Generate OpenAPI Spec

Convert the EDD's concise API design into a full OpenAPI 3.x specification.

- Input: API endpoints from EDD's Technical Design section
- Output: `docs/openapi.yaml`
- Expand each endpoint into complete OpenAPI format: parameters, request/response schemas, error codes, examples
- This spec becomes the authoritative API contract for implementation

## Phase 3: Implementation Plan

Create `docs/implementation-plan.md` using [template](assets/implementation-plan-template.md).

Determine optimal implementation order based on dependencies. Common patterns:
- Config → Models → Repository → Service → API
- Shared utilities → Core logic → Integration points

**Important:**
- Include checkbox for each task to track progress
- Delete after implementation complete

## Phase 4: Code Architecture Document

Create `docs/codebase-guide.md` using [template](assets/codebase-guide-template.md).

Document:
- Directory structure
- Layer architecture (API → Service → Repository → DB)
- Key components and their responsibilities
- Data flow
- Common patterns used

This document helps future developers understand the codebase without reading all code.

**Avoid duplicating EDD content.** EDD covers system design decisions; this document focuses on code-level structure and patterns.

## Phase 5: Implement (TDD)

Use `/test-driven-development` and `/software-architecture` skills for implementation.

**Language-specific guidance:** Check `references/<language>.md` if available (e.g., `references/go.md`, `references/rust.md`).

Follow strict TDD for each task in the implementation plan:

```
┌─────────────────────────────────────────────────┐
│  1. Write test (RED)                            │
│     - Define expected behavior                  │
│     - Test should fail initially                │
├─────────────────────────────────────────────────┤
│  2. Implement (GREEN)                           │
│     - Write minimal code to pass test           │
├─────────────────────────────────────────────────┤
│  3. Refactor                                    │
│     - Clean up while keeping tests green        │
├─────────────────────────────────────────────────┤
│  4. Verify                                      │
│     - Run ALL tests, ensure all pass            │
│     - Check coverage >= 85%                     │
├─────────────────────────────────────────────────┤
│  5. Mark task complete                          │
│     - Update checkbox in implementation-plan.md │
├─────────────────────────────────────────────────┤
│  6. Wait for user review                        │
│     - Report what was implemented and tested    │
│     - STOP and wait for user approval           │
│     - Do NOT proceed to next task until user    │
│       explicitly confirms to continue           │
└─────────────────────────────────────────────────┘
```

**Rules:**
- Never proceed to next task until current task's tests pass
- Never proceed to next task without explicit user approval
- Every function must have corresponding unit test
- Run full test suite after each task completion

## Phase 6: Finalize

1. **Verify test coverage** > 85%
2. **Update `docs/codebase-guide.md`** if architecture changed during implementation
3. **Delete `docs/implementation-plan.md`**
4. **Final test run** - all tests must pass

## References

- [Implementation Plan Template](assets/implementation-plan-template.md)
- [Codebase Guide Template](assets/codebase-guide-template.md)
