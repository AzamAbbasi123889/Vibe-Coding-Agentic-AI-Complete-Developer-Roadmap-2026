# Prompt Library

**Plan:** "Read SPEC.md. Propose architecture, file list and build order. List risks and assumptions. No code yet."

**Implement step:** "Implement step N of the plan only. Keep changes minimal. Explain each file in one line."

**Explain code:** "Explain @file to a beginner. Then list three ways it could fail."

**Debug:** "Goal: X. Actual: Y. Error: <paste>. Code: <paste>. Give 3 ranked hypotheses and the quickest check for each."

**Tests first:** "Write pytest tests for <behaviour>, including edge cases: empty, null, large, unicode. Do not implement yet."

**Refactor safely:** "Refactor @file to reduce duplication. Behaviour must stay identical. Existing tests must pass. Show the diff."

**Security review:** "Act as a security reviewer. Audit for injection, XSS, auth flaws, secrets, unsafe defaults. Findings with severity, location, fix. No code changes."

**Performance:** "Find the slowest part of this code path. Suggest measurements before optimisations."

**README:** "Write a README: purpose, screenshot placeholder, setup, env variables, commands, architecture overview, limitations."

**Commit message:** "Summarise this diff as a conventional commit message and a 3-line body."

**Handoff:** "Summarise progress for a fresh session: goal, decisions, files changed, working, broken, next step. Under 200 words."

**Learn:** "I do not understand <concept> in this code. Teach me with a small example, then quiz me with 3 questions."
