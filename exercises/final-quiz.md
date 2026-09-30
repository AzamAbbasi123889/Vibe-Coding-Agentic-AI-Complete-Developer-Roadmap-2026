# Final Quiz (self-check)

1. What are the five steps of the vibe coding loop?
2. Name three risks of accepting AI code without review.
3. What does ROGCO stand for?
4. Why commit before a large agent change?
5. What belongs in a rules file, and what does not?
6. What is MCP and what is one safety rule when using it?
7. Why is deleting a leaked key from your repo not enough?
8. What is the difference between authentication and authorisation?
9. Why should API keys for LLMs stay on the server?
10. What is prompt injection, and how can you reduce its impact?
11. When should you revert instead of asking the AI to fix again?
12. Name two signs a package suggested by AI might be unsafe.

## Answer key (short)
1. Describe, generate, run, review, refine.
2. Security holes, silent bugs, fake dependencies, unmaintainable code, leaked secrets.
3. Role, Output, Goal, Context, Other rules.
4. So you can roll back if the change is wrong or destructive.
5. Stack, commands, conventions, rules, architecture notes. Not secrets, long essays or outdated info.
6. Model Context Protocol; connects AI tools to external systems. Use only trusted servers with least privilege.
7. It remains in Git history and may already be copied. Revoke and rotate the key.
8. Authentication verifies identity; authorisation controls permissions.
9. Client-side keys can be stolen from the browser and abused.
10. Untrusted text that tries to steer the model. Treat input as data, limit tool powers, validate outputs.
11. After about two failed attempts, or when the code has become confusing.
12. Unknown publisher, very few downloads, name resembling a popular package, no repository, recently created.
