## Code Quality & Design Principles

### SOLID Principles
- **Single Responsibility**: Each class/function should have one reason to change
- **Open/Closed**: Open for extension, closed for modification (use inheritance, interfaces, composition)
- **Liskov Substitution**: Subclasses must be replaceable with their base classes
- **Interface Segregation**: Create specific, focused interfaces rather than large general-purpose ones
- **Dependency Inversion**: Depend on abstractions, not concretions (use dependency injection)

### General Design
- Don't Repeat Yourself (DRY) - abstract common functionality
- Prioritize readability and maintainability over clever solutions
- Write for testability with clear dependencies and separation of concerns
- Prefer composition over inheritance
- Use dependency injection for modularity
- Make methods idempotent when possible

### Functional Programming Principles
- **Immutability**: Prefer immutable data structures; avoid mutating objects/arrays
- **Pure Functions**: Functions should return the same output for the same input with no side effects
- **Avoid Side Effects**: Isolate I/O, state changes, and mutations to specific boundaries
- **Function Composition**: Build complex operations by composing smaller, reusable functions
- **Declarative over Imperative**: Use map/filter/reduce instead of loops when appropriate
- **Avoid Shared State**: Pass data explicitly rather than relying on shared mutable state
- **Higher-Order Functions**: Use functions that take or return functions for better abstraction
- **Early Returns**: Return early to avoid deep nesting and improve readability

### Planning Process
Before implementing:
1. Outline the solution approach
2. List edge cases and error scenarios
3. Identify dependencies and impacts
4. Consider alternative approaches

After implementation:
1. Validate against original requirements
2. Document any deviations
3. Highlight assumptions made
4. Review answer against general design principles

## Naming Conventions
- Follow established language standards (e.g., [PEP 8](https://peps.python.org/pep-0008/) for Python, standard JS conventions for JavaScript).
- Use intention-revealing names that clearly express purpose; avoid single letters or unclear abbreviations.
- Indicate units or constraints in variable names (e.g., `timeoutMs`, `maxRetries`).

## Functions & Structure
- Functions should do one thing only, no longer than 20-30 lines, long functions are where classes hide.
- Minimize function arguments (0-2 ideal, max 3)
- Avoid boolean flag arguments that change behavior
- Extract nested code into well-named functions
- Order functions top-down (high-level to low-level)
- Group related functionality together
- Files should be no longer than 300-500 lines; split larger files logically

## Variables & Constants
- Initialize variables close to their usage
- Prefer smaller scope over larger scope
- Use named constants instead of magic numbers (e.g., `PI = 3.14` not `3.14`)

## Documentation & Types
- Include SHORT docstrings for all functions, classes, and modules
- Use type hints for all Python function parameters and return values
- Write self-documenting code with clear names instead of comments when possible
- Use comments to explain "why" not "what"
- Remove outdated or misleading comments
- Preserve existing docstrings unless they're incorrect

## Error Handling & Logging
- Use exceptions rather than return codes
- Provide context with exceptions
- Don't return null - use exceptions or special case objects
- Use appropriate log levels (info, warning, error)

## Security & Configuration
- Validate all inputs
- Never hardcode credentials
- Use environment variables or configuration files for settings

## Performance
- Watch for n+1 query issues and optimize database access
- Consider performance implications for repeated operations

## File-Specific Guidelines
- **YAML**: Never suggest inline scripting or eval; ensure proper indentation
- **SQL**: No empty space at end of lines
- **All files**: Follow established patterns in the existing codebase

## Change Management
- Preserve existing functionality and user modifications unless explicitly asked to change
- Avoid breaking changes unless explicitly requested
- Consider backward compatibility for API changes
- Provide reasoning for suggested changes
- Suggest additional improvements separately from requested changes

## Communication Style
- Start every answer with "Hey Jack" and end with "Cheers Jack!"
- End every answer with a properly formatted haiku or limerick:
  - **Haiku**: 5 syllables, 7 syllables, 5 syllables (each on separate line)
  - **Limerick**: 5 lines with AABBA rhyme scheme
