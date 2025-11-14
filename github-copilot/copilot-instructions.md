# GitHub Copilot Instructions

## Project Overview
<!-- Describe your project here -->
This is a [PROJECT TYPE] project that [MAIN PURPOSE].

## Code Style and Standards

### General Guidelines
- Follow [STYLE_GUIDE] coding standards
- Write clear, self-documenting code
- Prefer readability over cleverness
- Use meaningful variable and function names

### Language-Specific Guidelines

#### Python
- Follow PEP 8 style guide
- Use type hints for all functions
- Prefer `pathlib` over `os.path`
- Use f-strings for string formatting
- Write docstrings in Google style

#### JavaScript/TypeScript
- Use ESLint configuration in this project
- Prefer `const` over `let`, avoid `var`
- Use async/await over promises chains
- Write JSDoc comments for public APIs
- Use TypeScript strict mode

#### Java
- Follow Google Java Style Guide
- Use meaningful names for variables and methods
- Prefer composition over inheritance
- Write Javadoc for public methods and classes

### File Organization
<!-- Describe your project structure -->
- `/src` - Source code
- `/tests` - Test files
- `/docs` - Documentation
- Keep files focused and single-purpose

## Testing

### Test Requirements
- Write unit tests for all new functions
- Aim for [X%] code coverage
- Use [TEST_FRAMEWORK] for testing
- Test edge cases and error conditions
- Make tests readable and maintainable

### Test Naming
- Use descriptive test names that explain what is being tested
- Format: `test_<function>_<scenario>_<expected_outcome>`

## Documentation

### Code Comments
- Write comments for complex logic
- Explain "why", not "what"
- Keep comments up-to-date with code changes
- Use TODO comments for future improvements

### Documentation Requirements
- Document all public APIs
- Include usage examples
- Explain parameters and return values
- Note any side effects or exceptions

## Security

### Security Practices
- Never commit secrets or API keys
- Validate all user inputs
- Use parameterized queries for database operations
- Follow OWASP security guidelines
- Keep dependencies updated

## Dependencies

### Adding Dependencies
- Prefer well-maintained, popular libraries
- Check license compatibility
- Avoid dependencies with known vulnerabilities
- Document why each dependency is needed

## Git Practices

### Commit Messages
- Use clear, descriptive commit messages
- Format: `<type>: <description>`
- Types: feat, fix, docs, style, refactor, test, chore

### Branch Naming
- Format: `<type>/<short-description>`
- Examples: `feature/user-authentication`, `fix/memory-leak`

## Specific Instructions for Copilot

When generating code for this project:

1. **Always** follow the project's existing patterns and conventions
2. **Prefer** using existing utility functions over creating new ones
3. **Include** appropriate error handling
4. **Add** type annotations (Python, TypeScript)
5. **Write** tests alongside implementation code
6. **Consider** performance implications for data-intensive operations
7. **Use** the project's logging framework for debug output
8. **Avoid** introducing new dependencies without discussion
9. **Keep** functions small and focused (< 50 lines)
10. **Document** public APIs with examples

## Project-Specific Context

### Technology Stack
- [List your main technologies]
- [Frameworks and libraries]
- [Development tools]

### Architecture Patterns
- [e.g., MVC, Microservices, Event-Driven]
- [Design patterns commonly used]

### Common Tasks
<!-- Examples of common development tasks in this project -->
- [Task 1 and how to approach it]
- [Task 2 and how to approach it]

## Examples

### Good Code Example
```python
def calculate_discount(price: float, discount_percentage: float) -> float:
    """
    Calculate the final price after applying a discount.
    
    Args:
        price: The original price (must be positive)
        discount_percentage: Discount as percentage (0-100)
    
    Returns:
        The final price after discount
    
    Raises:
        ValueError: If price is negative or discount is invalid
    """
    if price < 0:
        raise ValueError("Price must be positive")
    if not 0 <= discount_percentage <= 100:
        raise ValueError("Discount must be between 0 and 100")
    
    discount_amount = price * (discount_percentage / 100)
    return price - discount_amount
```

### Bad Code Example (Avoid)
```python
def calc(p, d):  # Unclear function and parameter names
    return p - p * d  # No input validation, no documentation
```

## Additional Notes

<!-- Add any project-specific notes or special requirements -->
- [Special consideration 1]
- [Special consideration 2]
- [Link to additional documentation]
