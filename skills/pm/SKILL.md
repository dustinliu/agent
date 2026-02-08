---
name: pm
description: "Product Manager skill for creating and maintaining product documentation. Use when the user needs to: (1) Write or update a PRD (Product Requirements Document), (2) Generate user stories from requirements or features, (3) Analyze and break down product requirements, or (4) Create acceptance criteria. Triggers include phrases like 'write a PRD', 'create user stories', 'analyze requirements', 'break down this feature', or 'document this product'."
---

# PM (Product Manager)

Help users create structured product documentation including PRDs, user stories, and requirements analysis.

## Core Capabilities

### 1. PRD Creation & Maintenance

Create or update Product Requirements Documents.

**Workflow:**
1. Gather context about the product/feature
2. Define goals and objectives
3. List functional and non-functional requirements
4. Output structured PRD in Markdown

**Template:** See [references/prd_template.md](references/prd_template.md) for the complete PRD structure.

**Example request:** "Write a PRD for a user notification system"

### 2. User Story Generation

Generate well-structured user stories from requirements or feature descriptions.

**Workflow:**
1. Understand the feature or requirement
2. Identify affected user personas
3. Break down into independent, valuable stories
4. Write acceptance criteria using Given-When-Then format
5. Assign priority (P0/P1/P2)

**Guide:** See [references/user_story_guide.md](references/user_story_guide.md) for user story format and INVEST criteria.

**Example request:** "Generate user stories for a shopping cart feature"

### 3. Requirements Analysis

Analyze and structure raw requirements into actionable items.

**Workflow:**
1. Review the raw requirements or feature request
2. Identify ambiguities and ask clarifying questions
3. Categorize into functional vs non-functional requirements
4. Identify dependencies and risks
5. Prioritize using P0/P1/P2 framework

**Example request:** "Analyze these requirements and identify gaps"

## Core Principle: Technology-Agnostic Documentation

**PRDs and User Stories must remain free of technical implementation details.**

- **Focus on "What" not "How"** - Describe the problem and desired outcome, never the implementation
- **No technical constraints** - Do not prescribe databases, frameworks, APIs, or architecture
- **Use business language** - Write from the user's perspective, not the developer's
- **Preserve implementation flexibility** - Let engineering teams choose the optimal technical solution

This separation ensures:
- Engineers can select the best technical approach without artificial constraints
- Requirements remain valid even when technology changes
- Better collaboration between PM and engineering through proper discussion

## Output Guidelines

- Output all documents in Markdown format
- Include clear priority levels (P0 = must have, P1 = should have, P2 = nice to have)
- Write acceptance criteria in Given-When-Then format
- Keep language specific and measurable; avoid vague terms
- Link related docs (design specs, technical docs, research)
- **Never include technical implementation details** - no mention of specific technologies, databases, or architecture

### Technology-Agnostic Examples

❌ **Avoid:**
- "Store data in PostgreSQL with Redis caching"
- "Use React components with Redux state management"
- "Implement REST API with JWT authentication"

✅ **Instead write:**
- "Data must persist reliably and be retrievable within 200ms"
- "Users can view and interact with their dashboard in real-time"
- "System must authenticate users securely"

## References

- [PRD Template](references/prd_template.md) - Complete PRD structure and writing tips
- [User Story Guide](references/user_story_guide.md) - Story format, INVEST criteria, and examples
