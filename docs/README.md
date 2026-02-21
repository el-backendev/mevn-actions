# MEVN Actions Starter Kit

This repository provides a minimal MEVN stack (MongoDB, Express, Vue, Node.js) boilerplate with GitHub Actions workflows for CI/CD.

## Why choose Actions for your workflow?

- **Automation**: Save time by letting GitHub handle repetitive tasks.
- **Consistency**: Ensure every build, test, and deploy follows the same rules.
- **Confidence**: Catch bugs and vulnerabilities before they reach production.

## Project Structure

```
mevn-actions/
├── client/          # Vue 3 + Vite frontend
│   ├── src/
│   │   ├── components/
│   │   │   └── __tests__/
│   │   ├── App.vue
│   │   └── main.js
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js
│   └── vitest.config.js
├── server/          # Express backend
│   ├── src/
│   │   ├── __tests__/
│   │   ├── app.js
│   │   └── index.js
│   ├── .env.example
│   └── package.json
├── .github/
│   └── workflows/   # CI/CD workflows
└── docs/            # Documentation
```

## Included Workflows

- **CI Pipeline** (`ci.yml`): Runs ESLint and tests on every push/PR.
- **Build Workflow** (`build.yml`): Compiles the Vue frontend automatically on push to main.
- **Deploy Workflow** (`deploy.yml`): Template for deployments (manual trigger only — configure secrets before use).
- **Security Workflow** (`security.yml`): Runs CodeQL analysis for vulnerabilities in JavaScript and TypeScript.

## Getting Started

1. Clone the repository and install dependencies:
   ```bash
   npm install
   ```
2. Copy `server/.env.example` to `server/.env` and fill in the values.
3. Configure secrets in GitHub repository settings for deployment (e.g., `HEROKU_API_KEY`, `RENDER_API_KEY`).
4. Push your code and watch the workflows run.

## Brainstorming Questions

- Why is CI important for small teams as well as large ones?
- When should you trigger deploys automatically, and when should you hold them back?
- How can security scans be integrated without slowing down development?
- What happens if you skip automation entirely?
- Should builds run on every branch, or only on main?
- Is deploying every commit sustainable, or should you prefer tagged releases?

---

This starter kit is not just about automation — it's about **thinking critically** about your workflow. Use these files as a foundation, and adapt them to your own needs.
