# Module 07: Hands-On Tutorials

Three tutorials, one per tool category. Do at least two. Each builds a small, real thing.

---

## Tutorial A: App builder. "Habit Tracker" in under an hour

**Tools:** any app builder (Lovable, Bolt.new, Replit Agent, etc.)

1. Open the tool and start a new project.
2. Paste this first prompt:

```
Build a habit tracker web app.
- Add a habit with a name and color
- A grid showing the last 14 days; click a day to mark done
- Show the current streak for each habit
- Clean, mobile-friendly design, light and dark mode
- Store data in the browser (localStorage) for now
Start simple; do not add login.
```
3. Test it. List three things you dislike.
4. Iterate one change at a time:
   - "Add a weekly completion percentage under each habit."
   - "Add an empty state with a friendly message."
   - "Let me delete a habit with a confirmation dialog."
5. Connect the project to GitHub (most builders offer this) and commit.
6. **Reflect:** Open the generated code. Find where habits are stored. Explain it in your journal.

**Stretch:** Ask the tool to add a real database and login, then review what it created.

---

## Tutorial B: AI editor. "Notes API + UI"

**Tools:** Cursor, Windsurf, or VS Code with Copilot / Cline

1. Create a folder and open it in the editor:
```bash
mkdir notes-app && cd notes-app && git init
```
2. Create `SPEC.md`:
```markdown
# Notes app
- Create, read, update, delete notes (title, body, created_at)
- Python FastAPI backend, SQLite storage
- Simple HTML page that lists notes and has a form
- Tests with pytest
Not now: auth, tags, search
```
3. In the chat/agent panel:
> "Read SPEC.md. Propose a file structure and build plan. Do not write code yet."
4. Approve or adjust the plan, then:
> "Implement step 1: project setup, dependencies in requirements.txt, and a health-check endpoint. Explain each file briefly."
5. Run it:
```bash
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```
6. Continue slice by slice: DB model, CRUD endpoints, tests, HTML page.
7. After each slice: run, test, commit.
8. Add a rules file (Module 06) and a `.env.example`.

**Checkpoint questions:** Which files did the AI create? Which would you delete? Where is input validated?

---

## Tutorial C: Terminal agent. "Test-fix loop on a messy script"

**Tools:** Claude Code, Gemini CLI, Codex CLI, or Aider

1. Create a deliberately flawed script `stats.py`:
```python
def average(nums):
    return sum(nums) / len(nums)

def median(nums):
    nums.sort()
    return nums[len(nums)//2]

def mode(nums):
    return max(nums, key=nums.count)
```
2. Commit it: `git add . && git commit -m "baseline"`
3. Start your agent in the folder and prompt:
> "Write pytest tests for stats.py covering normal cases and edge cases (empty list, even-length list for median, ties for mode). Run the tests. Report failures. Do not fix yet."
4. Observe: which bugs did the tests expose?
5. Then:
> "Fix stats.py so all tests pass without changing test expectations. Keep the functions pure (no mutating inputs). Show the diff."
6. Review the diff. Run `pytest`. Commit.
7. **Safety practice:** note which commands the agent asked permission for. Deny one on purpose and observe how it adapts.

---

## Tutorial D (optional): From screenshot to UI
1. Screenshot a simple website you admire (for learning only; do not copy branding).
2. Give it to a vision-capable tool: "Recreate this layout in React + Tailwind. Use placeholder text and images. Make it responsive."
3. Iterate on spacing, colors, components.
4. Replace the design with your own identity and content.

## Deliverable
Push at least two tutorial projects to GitHub with a README describing what you built and what you learned.
