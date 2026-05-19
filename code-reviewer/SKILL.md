---
name: code-reviewer
description: >
  Review code for bugs, security vulnerabilities, logic errors, performance issues, and style violations.
  Use when user pastes code and asks for a review, says "review my code", "check this code",
  "what s wrong with this", "find bugs", "audit my code", or shares code asking for feedback.
---
# Code Reviewer

## Severity Levels
- CRITICAL - Security vulnerabilities, data loss, crashes
- HIGH - Logic errors, incorrect behavior, major perf issues
- MEDIUM - Code smell, maintainability, minor perf
- LOW - Style, naming, minor improvements

## What to Check
### Security
- SQL injection, XSS, CSRF
- Hardcoded secrets, API keys
- Missing input validation
- Auth/authorization gaps

### Logic
- Off-by-one errors
- Null/undefined handling
- Edge cases
- Race conditions

### Performance
- N+1 queries
- Unnecessary loops
- Memory leaks

### Quality
- Dead code
- Duplicated logic
- Missing error handling

## Output Format
## Code Review
### Summary
[2-3 sentence assessment]
### Issues Found
CRITICAL: [issue] - Location: [where] - Fix: [code]
HIGH: ...
### Strengths
### Overall Score: X/10
