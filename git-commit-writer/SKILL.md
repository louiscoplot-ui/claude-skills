---
name: git-commit-writer
description: >
  Write conventional commit messages by analyzing staged git changes or code diffs.
  Use when user says "write a commit message", "commit message for this", pastes a git diff,
  or asks for help with git commits.
---
# Git Commit Writer

## Format
<type>(<scope>): <description>
[optional body]
[optional footer]

## Types
- feat - new feature
- fix - bug fix
- docs - documentation only
- style - formatting no logic change
- refactor - restructure no feature/fix
- perf - performance
- test - adding/fixing tests
- chore - build deps tooling
- ci - CI/CD changes

## Rules
1. Subject max 72 chars
2. Imperative mood: "add feature" not "added"
3. No period at end
4. Body explains WHY not WHAT
5. BREAKING CHANGE: in footer

## Examples
feat(auth): add Google OAuth login
fix(api): handle null response from endpoint
refactor(scraper): extract pagination into separate function
chore(deps): update playwright to 1.40.0

Provide commit message in code block, ready to copy-paste.
