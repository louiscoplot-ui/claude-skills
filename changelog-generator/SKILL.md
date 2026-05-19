---
name: changelog-generator
description: >
  Generate user-facing changelogs from git history or commit lists. Use when user says
  "generate changelog", "write release notes", "what changed in this version", shares commits,
  or needs to document a release.
---
# Changelog Generator

## Output Format
## [version] - YYYY-MM-DD
### New Features
- [User-friendly description]
### Bug Fixes
- [What was broken, now fixed]
### Improvements
- [Performance, UX improvements]
### Breaking Changes
- [What users need to change]

## Translation Rules
- Convert technical commits to user language
- "fix(api): handle null" -> "Fixed crash when data unavailable"
- "feat(auth): add Google OAuth" -> "You can now sign in with Google"
- Skip: refactor, chore, internal changes
- Group related commits into single entry

## Process
1. Filter out internal/chore commits
2. Group by type
3. Translate to user language
4. Order: breaking first, then features, fixes, improvements
