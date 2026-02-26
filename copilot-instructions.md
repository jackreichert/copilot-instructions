## General Design & Structure
- Functions: one responsibility, 20–30 lines max
- If a method gets overly complex, refactor it
- Files ≤ 300–500 lines; split logically
- DRY: abstract common functionality
- Prioritize readability & maintainability over cleverness
- Favor composition + dependency injection over inheritance
- Minimize args (0–2 ideal, ≤3), avoid boolean flags
- Extract nested logic → well-named functions
- Top-down order: high-level → low-level
- Make methods idempotent when reasonable
- Prefer the scalpel to the sledgehammer: targeted changes > large rewrites
​
### SOLID Principles
- **Single Responsibility**: one reason to change
- **Open/Closed**: open for extension, closed for modification
- **Liskov Substitution**: subclasses fully replaceable
- **Interface Segregation**: small, focused interfaces
- **Dependency Inversion**: depend on abstractions (use DI)
​
### Functional Programming Principles
- Prefer immutability & pure functions
- Isolate side effects (I/O, state) to boundaries
- Compose small reusable functions
- Declarative > imperative (map/filter/reduce over loops)
- Avoid shared mutable state
- Use early returns to reduce nesting
​
## Planning Process
Before ANY code change (REQUIRED - never skip):
1. Understand existing buisness logic & requirements
2. Outline approach  
3. List edge cases & errors  
4. Identify dependencies  
5. Consider alternatives  
​
After EVERY code change (REQUIRED - never skip):
1. Validate requirements against new and old buisness logic
2. Document deviations & assumptions  
3. Check against design principles  
4. Include Big-O analysis
​
## Naming, Documentation & Types
- Follow established language standards ([PEP 8](https://peps.python.org/pep-0008/) for Python, [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) for JavaScript/TypeScript).
- Intention-revealing names, no magic numbers
- Units/constraints in names (`timeout_ms`, `max_retries`)
- Small scope, init vars near usage
- Short docstrings for all public items
- Type hints everywhere possible
- Comments explain **why**, not **what**, only comment when a WHY is needed.
​
## Error Handling & Robustness
- Fail fast: raise meaningful exceptions early
- Never silently swallow exceptions
- Prefer specific exceptions over `Exception`
- No `None`/magic values for errors → raise or Result pattern
- Log appropriately (debug/info/warn/error)
​
## Security & Configuration
- Validate/sanitize **all** external input
- Never commit secrets → env vars / secret manager
- Least privilege everywhere
- Use strong password hashing (Argon2id/bcrypt)
- Pin deps & audit regularly
​
## Performance & Scalability
- Know your big-O — avoid nested loops, N+1 queries
- Cache wisely, invalidate correctly
- Profile before deep optimization
- Use right data structures (`set`, `deque`, generators)
​
## Testing
- Tests in parallel with code (prefer TDD)
- ≥80% coverage on core logic
- One assertion per test
- Fast deterministic unit tests > slow integration
- Mock only externals, never own code
​
## Change Management
- Preserve existing behavior unless requested
- Avoid breaking changes
- Explain all suggestions
- Separate nice-to-haves from requirements
​
## Context Sharing
- See [Workflow Guide](workflow-guide.md) for detailed instructions
- Quick summary: maintain lightweight CONTEXT.md + detailed docs in /context/
​
## Communication Style
- Start every answer with "Hey Jack" and end with "Cheers Jack!"
- End every answer with a properly formatted haiku or limerick:
  - **Haiku**: 5 syllables, 7 syllables, 5 syllables (each on separate line)
  - **Limerick**: 5 lines with AABBA rhyme scheme