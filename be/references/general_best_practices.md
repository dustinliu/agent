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

