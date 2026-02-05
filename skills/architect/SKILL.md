---
name: architect
description: >
  Backend system design and documentation workflow. Covers API design, database schema,
  and EDD (Engineering Design Document) writing. Use when designing backend systems or APIs,
  writing or reviewing EDDs, or planning database schemas. This skill is DESIGN ONLY - it
  does NOT write implementation code (Golang, JavaScript, Python, etc.). For implementation,
  use the backend-engineer skill. Triggers include "design an API", "write an EDD",
  "database schema design", "system architecture".
---

# Architect

Design and document backend systems. This skill covers: requirements analysis → system design → EDD.

## Scope

**Do:**
- API contract design (endpoints, request/response schemas)
- Database schema design (tables, relationships, indexes)
- Architecture diagrams (Mermaid)
- Technical decision documentation

**Do NOT:**
- Write implementation code (Golang, JavaScript, Python, etc.)
- For implementation, hand off to `backend-engineer` skill

**IMPORTANT: Never assume. Always ask.**
- If there are ANY questions about requirements or design decisions, discuss with the user first. Do not make assumptions about what the user wants.
- For important technical decisions, propose at least 2 suitable options with trade-offs, then discuss with the user before proceeding.

## Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                    1. REQUIREMENTS ANALYSIS                     │
│  Clarify scope, constraints, and success criteria               │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    2. SYSTEM DESIGN                             │
│  Architecture, API contracts, database schema                   │
│  → Use /architecture skill                                      │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    3. WRITE EDD                                 │
│  Document design decisions and trade-offs                       │
│  → See: references/edd-template.md                              │
└─────────────────────────────────────────────────────────────────┘
```

## Phase 1: Requirements Analysis

Before designing, clarify:

- **Problem**: What exactly are we solving?
- **Users**: Who uses this? How many? (scale implications)
- **Constraints**: Performance, security, compliance requirements
- **Integration**: What existing systems must this work with?
- **Timeline**: MVP scope vs full feature set

Output: Clear problem statement and scope definition.

## Phase 2: System Design

Use the `/architecture` skill for system design guidance.

Key decisions:
- Tech stack (language, framework, database, infrastructure)
- Architecture pattern (monolith vs microservices)
- API design (endpoints, request/response schemas)
- Database design (tables, relationships, indexes)
- Caching and queue strategy

## Phase 3: Write EDD

Document the design formally. Use the [EDD template](references/edd-template.md).

Key sections:
1. Problem & Goals
2. Proposed Solution (architecture, API, DB)
3. Testing Strategy
4. Open Questions

Best practices:
- Keep it concise - readers should understand in < 10 minutes
- Be specific - include actual API contracts, not just descriptions
- Address trade-offs - show alternatives considered
- Define success metrics

### Mermaid Diagrams

**Must use Mermaid for:**
- High-Level Architecture (system diagrams, component interactions)
- Database Schema (erDiagram)
- Data flow

**Use when complex:**
- API call sequences (sequence diagram) - when flow involves multiple services
- Rollout decision flow - when multiple conditional branches exist

## References

- [EDD Template](references/edd-template.md) - Engineering Design Document structure
- `/architecture` skill - System design guidance
