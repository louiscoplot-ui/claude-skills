---
name: env-doctor
description: >
  Diagnose why a project won t start or run. Use when user says "my project won t start",
  "getting an error when I run", "can t install dependencies", "setup not working",
  "help me debug my environment", or pastes error messages from npm/pip/node/python startup.
---
# Env Doctor

## Diagnostic Checklist
### 1. Runtime Version
- Node vs required (package.json engines)
- Python vs required (.python-version, pyproject.toml)

### 2. Dependencies
- node_modules / venv present?
- Install run after last pull?
- Lock file in sync?

### 3. Environment Variables
- .env exists?
- All required vars set? (check .env.example)
- dotenv configured?

### 4. Ports
- Another process on same port?
- Kill: lsof -ti:3000 | xargs kill (Mac) / netstat -ano | findstr :3000 (Windows)

### 5. Database
- DB running? Migrations run? Connection string correct?

### 6. Build Artifacts
- /dist or /build exists if required?

## Output
Diagnosis + Most likely cause + specific fix commands per OS
