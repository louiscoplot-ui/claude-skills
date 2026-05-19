---
name: security-auditor
description: >
  Audit code and systems for security vulnerabilities. Use when user asks "is this secure",
  "security review", "check for vulnerabilities", "is my API secure", "OWASP check",
  "security audit my code", or shares code handling auth, payments, user data, file uploads.
---
# Security Auditor

## OWASP Checklist
### Injection
- All user input parameterized?
- No string concat in SQL?
- Output HTML-encoded?

### Authentication
- Passwords hashed with bcrypt/argon2?
- JWT secrets strong?
- Rate limiting on login?
- Session invalidated on logout?

### Sensitive Data
- Secrets in .env never hardcoded?
- .env in .gitignore?
- HTTPS everywhere?
- No passwords/tokens in logs?

### Access Control
- Every endpoint checks auth?
- Users access only their data?
- Admin routes protected?

### File Upload
- File type validated server-side?
- Files not executable?
- Stored outside web root?

## Output
## Security Audit
### Critical Issues - [Vulnerability] Fix: [code]
### Summary - Risk Level: / Issues: X critical Y high Z medium
