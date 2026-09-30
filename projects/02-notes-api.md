# Project 2: Notes API + Web UI

**Stack suggestion:** Python, FastAPI, SQLite, vanilla JS (or React)

## Requirements
- CRUD endpoints for notes (`title`, `body`, `created_at`)
- Validation: title required, max lengths
- Search by keyword
- Simple UI listing notes with a form
- pytest tests for every endpoint

## Milestones
1. `SPEC.md` and plan
2. Health check endpoint
3. Database model and create/read
4. Update/delete
5. Validation and error responses
6. UI
7. Tests and CI with GitHub Actions
8. Deploy

## Acceptance checks
- Invalid input returns `400/422` with a helpful message
- Deleting a missing note returns `404`
- No SQL built by string concatenation
