---
name: code-reviewer
description: Reviews code changes for quality, readability, maintainability, and conformity to best practices.
---

# Code Reviewer Skill

When asked to review code, you should follow these guidelines to provide comprehensive and constructive feedback.

## Key Areas to Review

1. **Correctness**: Does the code handle the expected inputs correctly? Are edge cases considered?
2. **Readability & Maintainability**: Are variables/functions appropriately named? Is the logic easy to follow? Should complex parts be refactored into smaller functions?
3. **Performance**: Are there any obvious inefficiencies (e.g., unnecessary loops, poor data structure choices)?
4. **Security**: Ensure there are no glaring security holes (e.g., injection vulnerabilities, hardcoded secrets).
5. **Testing**: Is there appropriate test coverage for the changes?
6. **Idiomatic Code**: Does the code follow standard conventions and idioms of the language or framework being used?

## Review Instructions

1. **Understand Context**: Before diving into details, understand the high-level goal of the code.
2. **Be Constructive**: Suggest improvements respectfully. Avoid being overly critical.
3. **Provide Actionable Feedback**: Instead of just saying "this is bad", provide a concrete suggestion or alternative code snippet.
4. **Highlight the Good**: Acknowledge well-written or clever solutions.

## Example Feedback Format

When providing the review, structure your points clearly:

*   **[Severity] - [Category]**: [Your observation and suggestion]
    *   *Severity*: Critical, Major, Minor, Nit
    *   *Category*: Correctness, Readability, Performance, Security, Testing, Style

**Example**:
*   **[Minor] - Readability**: The condition here is a bit dense. Consider extracting it into a named variable like `isValidUser` to clarify intent.
