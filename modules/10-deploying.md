# Module 10: Deploying Your Project

## 10.1 From laptop to internet

```
Local code -> GitHub repo -> Hosting platform -> Public URL
```

## 10.2 Prepare the repo
- `README.md` with description, screenshots, setup, usage
- `.gitignore` (no `.env`, `node_modules`, `.venv`)
- `.env.example` listing required variables with fake values
- Dependencies declared (`package.json` or `requirements.txt`)
- Start/build commands documented

## 10.3 Push to GitHub
```bash
git remote add origin https://github.com/YOU/REPO.git
git branch -M main
git push -u origin main
```

## 10.4 Hosting options (categories)

| Type | Examples | Good for |
|------|----------|----------|
| Static/frontend hosting | Vercel, Netlify, Cloudflare Pages, GitHub Pages | Websites, React/Next/Vite apps |
| App/backend hosting | Render, Railway, Fly.io | APIs, full-stack apps, workers |
| Container/cloud | AWS, GCP, Azure | Scale and custom needs |
| Serverless | Vercel Functions, Cloudflare Workers, AWS Lambda | Small APIs, event handlers |

Free tiers change often and may sleep idle apps or limit usage. Check each provider's current docs.

## 10.5 Deploy a frontend (generic steps)
1. Create an account and choose **Import Git Repository**.
2. Select your repo; the platform detects the framework.
3. Confirm build command (e.g. `npm run build`) and output directory.
4. Add environment variables in the dashboard.
5. Deploy; every push to `main` redeploys automatically.

## 10.6 Deploy a Python API (generic steps)
1. Add `requirements.txt` and a start command, e.g. `uvicorn app.main:app --host 0.0.0.0 --port $PORT`.
2. Create a web service from your GitHub repo.
3. Set environment variables (secrets) in the dashboard.
4. Deploy and check logs.
5. Point your frontend at the deployed API URL; configure CORS to allow only your frontend domain.

## 10.7 Environment variables by environment
| Variable | Local | Production |
|----------|-------|------------|
| `DATABASE_URL` | sqlite file | managed Postgres URL |
| `DEBUG` | true | false |
| `ALLOWED_ORIGINS` | http://localhost:3000 | https://yourapp.example |

## 10.8 CI with GitHub Actions
Create `.github/workflows/ci.yml`:

```yaml
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"
      - run: pip install -r requirements.txt
      - run: pytest -q
```
Now every push runs your tests. AI can generate these workflows, but review permissions and secrets usage.

## 10.9 After deploy
- Test the live URL on phone and desktop
- Check logs for errors
- Add basic monitoring (uptime checks, error tracking)
- Back up data
- Write a short "Known limitations" section in the README

## Exercise
Deploy one project from Module 07 and add the live link and a screenshot to its README.
