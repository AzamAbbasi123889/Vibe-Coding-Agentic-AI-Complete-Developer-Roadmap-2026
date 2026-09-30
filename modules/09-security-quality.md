# Module 09: Security and Code Quality

AI-generated code is convincing, not automatically correct or safe. This module is the most important one for anything beyond a toy.

## 9.1 Top risks in AI-generated code

| Risk | What it looks like | Defence |
|------|--------------------|---------|
| Leaked secrets | API key in source, committed to GitHub | `.env`, `.gitignore`, secret scanning, rotate if leaked |
| SQL injection | `f"SELECT * FROM users WHERE id={uid}"` | Parameterised queries / ORM |
| XSS | Inserting user text into HTML unescaped | Framework escaping, avoid `innerHTML` |
| Broken auth | Client-side-only checks, weak sessions | Server-side checks on every request |
| Insecure defaults | Debug mode on, CORS `*`, open admin routes | Review config for production |
| Weak password handling | Plain text or fast hashes | bcrypt/argon2 via a vetted library |
| Fake dependencies | Package that does not exist or is malicious | Verify name, publisher, downloads, repo |
| Over-permissive agents | Tool runs destructive commands | Approve commands, use sandboxes, version control |
| Prompt injection | Untrusted text steers your AI feature or agent | Treat external content as data, limit tool powers |

## 9.2 Secrets handling
1. Never paste real keys into prompts or chats.
2. Put secrets in `.env`; add `.env` to `.gitignore` **before** the first commit.
3. If a key is ever committed: **revoke and rotate it immediately**. Deleting the file from history is not enough.
4. Use separate keys for development and production, with least privilege and spending limits.
5. Enable GitHub secret scanning and push protection.

## 9.3 Input is hostile
Every value from a user, URL, file or API is untrusted. Validate type, length, range and format on the **server**. Escape output. Use parameterised queries.

```python
# Bad
cursor.execute(f"SELECT * FROM users WHERE email = '{email}'")

# Good
cursor.execute("SELECT * FROM users WHERE email = ?", (email,))
```

## 9.4 Authentication and authorisation
- Do not build auth from scratch if you can avoid it: use a provider or a mature library.
- **Authentication**: who are you? **Authorisation**: what may you do?
- Check ownership on the server: user A must not read user B's record by changing an ID in the URL.

## 9.5 Dependency hygiene
```bash
npm audit          # JavaScript
pip list --outdated
pip install pip-audit && pip-audit
```
Pin versions, remove unused packages, and be suspicious of unfamiliar ones.

## 9.6 Safe agent practices
- Run agents on a **branch** with a clean working tree
- Prefer modes that **ask before** running commands and editing files until you trust the workflow
- Never give agents production database credentials
- Keep backups; test destructive migrations on copies
- Read commands before approving: watch for `rm -rf`, `curl | sh`, `chmod 777`, force pushes

## 9.7 Privacy and licensing
- Do not paste customer data, personal data or proprietary code into tools your organisation has not approved.
- Understand your tool's data policy (training opt-out, privacy mode, retention).
- AI output can resemble existing open-source code. For commercial projects, check licences of dependencies and consider your organisation's policy.

## 9.8 Quality checklist before shipping
- [ ] Runs from a clean clone using README instructions
- [ ] Tests pass; critical paths covered
- [ ] No secrets in repo or history
- [ ] Input validated and errors handled gracefully
- [ ] Dependencies audited
- [ ] Logging without sensitive data
- [ ] Production config reviewed (debug off, CORS restricted, HTTPS)
- [ ] You can explain how each major part works

## 9.9 Ask the AI to audit itself (then verify)
> "Act as a security reviewer. Audit these files for OWASP Top 10 issues, secret exposure, and unsafe defaults. List findings with severity, file/line, and a fix. Do not change code yet."

Treat the result as leads to verify, not as a clean bill of health.

## Exercise
Run the audit prompt on one of your projects and fix the top two findings. Record before and after in your journal.
