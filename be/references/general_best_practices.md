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
- **Ensure Unit Tests exist for all code changes**:
  - After modifying code, immediately create corresponding Unit Tests if they don't already exist.
  - Verify that the newly created Unit Tests pass successfully.
  - Do not proceed with further development until the Unit Tests for the changes are in place and passing.
- **Always verify Unit Tests after code changes**:
  - After any code modification, immediately run the relevant Unit Tests.
  - Ensure all existing tests pass before proceeding with further changes.
  - If tests fail, fix the issues before continuing development.
  - Do not skip test verification, even for minor changes.
