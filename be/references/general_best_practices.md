# General Coding Best Practices

## Library-First Approach
- **Always prioritize existing solutions**:
  - Check package registries (e.g., npm) or web search for available libraries.
  - Evaluate existing Service/SaaS solutions.
  - Consider third-party APIs for general functionality.
- **Use libraries instead of custom utilities**: For example, use `cockatiel` to handle retry logic instead of writing it yourself.
- **Write custom code only in the following scenarios**:
  - Domain-specific business logic.
  - Performance-critical paths with specific requirements.
  - External dependencies are overkill.
  - Security-sensitive code requiring full control.
  - Existing solutions are confirmed to be unsuitable after thorough evaluation.

## Testing Requirements

**MANDATORY**: Unit Tests are NOT optional. Every code change MUST have corresponding Unit Tests.

### Unit Test Creation (MANDATORY)
- **MUST create Unit Tests for ALL new OR modified logic**:
  - After writing OR modifying ANY function, method, or logic, you MUST immediately ensure corresponding Unit Tests exist.
  - If Unit Tests do NOT exist for the new or modified logic, you MUST create them immediately.
  - If Unit Tests already exist but do NOT cover the modified logic, you MUST update or add tests to cover the changes.
  - New or modified logic without Unit Test coverage is considered INCOMPLETE and UNACCEPTABLE.
  - Tests MUST cover:
    - Normal/happy path scenarios
    - Edge cases and boundary conditions
    - Error handling and failure scenarios
  - Do NOT proceed with any other tasks until Unit Tests are created/updated and verified.

### Unit Test Verification (MANDATORY)
- **MUST verify Unit Tests pass**:
  - After creating Unit Tests, you MUST run them to verify they pass successfully.
  - After ANY code modification, you MUST run the relevant Unit Tests to ensure existing tests still pass.
  - If tests fail, you MUST fix the issues immediately before continuing development.
  - Do NOT skip test verification, even for minor changes.

### Pre-Completion Checklist (MANDATORY)
Before marking any task as complete, you MUST verify:
1. ✅ All new or modified functions/methods have corresponding Unit Tests
2. ✅ All Unit Tests have been executed and pass successfully
3. ✅ Test output has been reviewed to confirm proper coverage of ALL changes
4. ✅ No new or modified logic exists without Unit Test coverage

**If ANY of the above items are not satisfied, the task is NOT complete.**
