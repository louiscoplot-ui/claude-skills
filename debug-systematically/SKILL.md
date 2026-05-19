---
name: debug-systematically
description: >
  Debug code errors and unexpected behavior systematically. Use when user shares an error message,
  stack trace, "this isn t working", "why is this breaking", "bug in my code", or any code
  producing wrong output. Works across Python, JavaScript, TypeScript, React, Flask, SQL.
---
# Debug Systematically

## Process
1. Understand: exact error, line, expected vs actual
2. Reproduce: consistent? minimal conditions?
3. Isolate: binary search, console.log at key points

## Common Culprits
### TypeError/AttributeError
- Variable is None when you expect a value
- Wrong type passed to function

### Async/Promise
- Missing await
- Race condition
- Promise not returned

### React
- State mutation (use spread)
- Missing useEffect dependency
- Key prop missing in lists

### SQL
- NULL handling
- JOIN producing duplicates
- Transaction not committed

## Output
## Debug Analysis
**Error:** [what s happening]
**Root Cause:** [why]
**Fix:** [code]
**Why this works:** [explanation]
**Also check:** [related issues]
