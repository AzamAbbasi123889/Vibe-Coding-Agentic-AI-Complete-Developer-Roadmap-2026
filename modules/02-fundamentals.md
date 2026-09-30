# Module 02: Fundamentals You Still Need

AI writes code, but you still need a mental map to steer it. This module is the minimum viable foundation.

## 2.1 The terminal

| Command | Meaning |
|---------|---------|
| `pwd` | Where am I? |
| `ls` (`dir` on Windows CMD) | List files |
| `cd folder` | Enter a folder |
| `mkdir name` | Make a folder |
| `cat file` / `type file` | Show a file |
| `rm file` | Delete a file (permanent!) |

AI agents run these commands for you, so you must recognise dangerous ones: `rm -rf`, `sudo`, `curl ... | sh`, `git push --force`, `DROP TABLE`.

## 2.2 Git in ten minutes

Git records snapshots of your project.

```bash
git init                     # start tracking
git status                   # what changed?
git add .                    # stage changes
git commit -m "Add login"    # save a snapshot
git log --oneline            # history
git restore file.py          # discard uncommitted edits to a file
git checkout -b feature/x    # new branch
git switch main              # back to main
git merge feature/x          # combine work
```

**Vibe coding rule:** commit *before* asking an agent for a large change. If it goes wrong: `git restore .` or `git reset --hard HEAD` (this discards uncommitted work, so use it deliberately).

### GitHub basics
```bash
git remote add origin https://github.com/YOU/REPO.git
git branch -M main
git push -u origin main
```

## 2.3 How the web works (essential map)

```
Browser (HTML, CSS, JavaScript)  <--HTTP-->  Server (API)  <-->  Database
```

- **Frontend**: what users see (HTML structure, CSS style, JS behaviour). Frameworks: React, Vue, Svelte, Next.js.
- **Backend**: logic and data access. Frameworks: Flask, FastAPI, Express, Django.
- **Database**: stored data. SQLite (simple), PostgreSQL (production), MongoDB (documents).
- **API**: a contract for asking a server to do things, usually over HTTP.

### HTTP verbs
| Verb | Purpose | Example |
|------|---------|---------|
| GET | Read | `GET /users/5` |
| POST | Create | `POST /users` |
| PUT/PATCH | Update | `PATCH /users/5` |
| DELETE | Remove | `DELETE /users/5` |

### Status codes
`200` OK, `201` Created, `400` bad request, `401` not logged in, `403` forbidden, `404` not found, `500` server bug.

## 2.4 JSON
```json
{ "name": "Asha", "skills": ["python", "sql"], "active": true }
```
Keys in quotes, values can be strings, numbers, booleans, arrays, objects, or null. You will see JSON everywhere.

## 2.5 Reading code (the skill that protects you)

Given any file, ask these five questions:
1. What is the **entry point**? (`main.py`, `index.js`, `app/page.tsx`)
2. What are the **inputs**? (user input, files, network, database)
3. What are the **outputs** or side effects? (screen, files, database writes, emails)
4. Where are the **decisions**? (`if`, `switch`, loops)
5. What could **go wrong**? (empty input, network failure, wrong type)

If you cannot answer these, ask the AI: *"Explain this file to a beginner. Then list three ways it could fail."*

## 2.6 Package managers and dependencies
- JavaScript: `npm install`, `package.json`
- Python: `pip install`, `requirements.txt`, virtual environments (`python -m venv .venv`)

Every dependency is code you did not write. AI sometimes invents package names that do not exist or that attackers register to exploit this. **Verify a package exists and is popular before installing.**

## 2.7 Environment variables
Secrets and settings live in a `.env` file, never in source code.
```
OPENAI_API_KEY=sk-...
DATABASE_URL=sqlite:///app.db
```
Add `.env` to `.gitignore`. Provide a `.env.example` with fake values.

## Exercises
See `exercises/module-02.md`.
