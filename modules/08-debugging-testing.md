# Module 08: Debugging and Testing with AI

## 8.1 The debugging loop
1. **Reproduce**: make the bug happen reliably
2. **Isolate**: smallest input or code that triggers it
3. **Hypothesise**: list likely causes
4. **Test the hypothesis**: logs, breakpoints, experiments
5. **Fix**: smallest change that resolves it
6. **Prevent**: add a test

AI helps at every step, but **you** must provide real evidence: error text, logs, versions, steps.

## 8.2 Reading an error message
```
Traceback (most recent call last):
  File "app.py", line 12, in <module>
    total = price * qty
TypeError: can't multiply sequence by non-int of type 'float'
```
- Last line: **what** went wrong
- Lines above: **where** (file, line, call chain)
- Usually the bottom-most frame in your own code is the place to look

## 8.3 Debug prompt template
```
Goal: <what should happen>
Actual: <what happens>
Error: <paste exact text>
Code: <relevant snippet or @file>
Environment: <language/framework versions, OS>
Tried: <what you did>
Ask: Give 3 ranked hypotheses and the quickest check for each.
```

## 8.4 Tools to use alongside the AI
| Tool | Use |
|------|-----|
| Browser DevTools (Console, Network) | Frontend errors, failed API calls |
| `print` / `console.log` | Quick state inspection |
| Debugger (VS Code breakpoints) | Step through logic |
| `curl` / Postman / Bruno | Test APIs independently of the UI |
| Logs | Production problems |

## 8.5 Testing basics
- **Unit tests**: one function in isolation
- **Integration tests**: several parts together (API + database)
- **End-to-end tests**: simulate a real user (Playwright, Cypress)

### Example (pytest)
```python
from stats import median

def test_median_odd():
    assert median([3, 1, 2]) == 2

def test_median_even():
    assert median([4, 1, 3, 2]) == 2.5

def test_median_empty():
    import pytest
    with pytest.raises(ValueError):
        median([])
```

## 8.6 AI and tests: the safe pattern
1. Describe behaviour in plain language.
2. AI writes tests **first**; you read them and confirm they match your intent.
3. Run them (they should fail).
4. AI implements; run again.
5. **Never let the AI change a test just to make it pass** without your approval.

## 8.7 Test smell list (AI-generated)
- Tests that assert nothing meaningful
- Tests that mirror the implementation line by line
- Over-mocking so nothing real is tested
- Snapshot tests approved blindly
- Missing edge cases: empty, null, huge, unicode, negative, duplicates, timezone boundaries

## 8.8 Manual verification checklist
- Try the happy path
- Try empty input and very long input
- Try invalid input and special characters
- Try double-clicking submit, refreshing mid-action, going offline
- Check mobile width

## Exercise
Take a buggy function from `exercises/module-08.md`, reproduce, write a failing test, then fix it with AI help.
