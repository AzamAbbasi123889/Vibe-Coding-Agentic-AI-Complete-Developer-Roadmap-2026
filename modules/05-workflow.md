# Module 05: The Professional Vibe Coding Workflow

## 5.1 The seven-step cycle

1. **Spec**: write what and why in a short `SPEC.md`
2. **Plan**: ask the AI for a step-by-step plan; edit it yourself
3. **Branch**: `git switch -c feature/<name>`
4. **Generate**: implement one step at a time
5. **Verify**: run, test, try edge cases
6. **Review**: read the diff, ask the AI to explain anything unclear
7. **Commit**: small, descriptive commits

## 5.2 Writing a mini spec

```markdown
# Feature: Expense tracker

## Problem
I forget where my money goes.

## Users
Just me, on my laptop.

## Must have
- Add expense (amount, category, date, note)
- List expenses, filter by month
- Monthly total per category

## Nice to have
- CSV export

## Not now
- Login, multi-user, mobile app

## Tech
Python + FastAPI + SQLite, simple HTML frontend.

## Done when
- I can add and list expenses
- Totals match a manual calculation for sample data
```

The "Not now" section is powerful: it stops scope creep, from you and from the AI.

## 5.3 Plan mode
Many tools have a planning or "architect" mode. Use it for anything larger than a single function. Ask:

> "Read the spec. Propose an architecture and a build order. List files you will create. Identify risks. Do not write code."

Edit the plan. Then say: "Implement step 1 only."

## 5.4 Commit discipline
- Commit **before** a big AI change (your safety net)
- Commit **after** each working step
- Use clear messages: `feat: add expense filter by month`, `fix: handle empty category`

```bash
git add -p        # review hunks interactively
git diff          # see what changed
git commit -m "feat: monthly totals"
```

## 5.5 Reviewing AI diffs: a checklist
- [ ] Does it do only what I asked?
- [ ] Any files touched that I did not expect?
- [ ] Any new dependencies? Are they real and necessary?
- [ ] Hard-coded secrets, URLs, or test data left in?
- [ ] Error handling present for input, network, and files?
- [ ] Anything deleted or overwritten?
- [ ] Do existing tests still pass?

## 5.6 Working in small vertical slices
Build the thinnest end-to-end path first (UI to API to database), then widen. This reveals integration bugs early.

```
Slice 1: add one expense via curl -> saved in DB
Slice 2: list expenses via API
Slice 3: simple HTML page shows the list
Slice 4: add form on the page
Slice 5: filters and totals
```

## 5.7 When the AI gets stuck
1. Stop. Do not keep sending "fix it".
2. Read the error yourself.
3. Revert to the last good commit.
4. Reduce the problem to the smallest reproduction.
5. Ask a fresh question with the evidence.
6. Try a different model or approach.
7. Consult official docs.

## Exercise
Write a `SPEC.md` for a project of your choice, get a plan from an AI, and commit both before any code.
