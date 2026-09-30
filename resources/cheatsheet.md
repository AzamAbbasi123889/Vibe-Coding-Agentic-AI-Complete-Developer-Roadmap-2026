# Vibe Coding Cheat Sheet

## Loop
Describe -> Generate -> Run -> Review -> Refine

## Before you prompt
- Clean Git state, new branch
- SPEC.md written
- Rules file present

## Prompt skeleton
```
Role: senior <language> engineer
Goal: <one outcome>
Context: <stack, files, versions>
Rules: <constraints, do-nots>
Output: plan first, then diff; add tests
```

## When stuck
Stop, read the error, revert, shrink the problem, ask with evidence, try another model.

## Review checklist
Scope OK? New deps? Secrets? Errors handled? Tests pass? Can I explain it?

## Git panic buttons
```bash
git status
git restore .          # discard uncommitted edits
git reset --hard HEAD  # discard all uncommitted work (careful)
git reflog             # find lost commits
```

## Never
Paste secrets, skip review, run unknown commands, ship unaudited auth code.
