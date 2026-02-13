# MEVN Actions Starter Kit

This repository provides a set of GitHub Actions workflows tailored for the MEVN stack (MongoDB, Express, Vue, Node.js).

## Why choose Actions for your workflow?

- **Automation**: Save time by letting GitHub handle repetitive tasks.
- **Consistency**: Ensure every build, test, and deploy follows the same rules.
- **Confidence**: Catch bugs and vulnerabilities before they reach production.

## Included Workflows

- **CI Pipeline**: Runs ESLint and tests on every push/PR.
- **Build Workflow**: Compiles the Vue frontend automatically.
- **Deploy Workflow**: Deploys your app to Heroku, Render, or GitHub Pages.
- **Security Workflow**: Runs CodeQL analysis for vulnerabilities in JavaScript and TypeScript.

## 📚 Documentação Adicional

- **[Lista Curada de Actions](./curated-actions.md)**: Catálogo completo de GitHub Actions recomendadas para MEVN, organizadas por domínio (CI, Build, Deploy, Security).

## Brainstorming Questions

- Why is CI important for small teams as well as large ones?
- When should you trigger deploys automatically, and when should you hold them back?
- How can security scans be integrated without slowing down development?
- What happens if you skip automation entirely?
- Should builds run on every branch, or only on main?
- Is deploying every commit sustainable, or should you prefer tagged releases?

## Getting Started

1. Copy the workflows into your project.
2. Configure secrets (e.g., `HEROKU_API_KEY`, `RENDER_API_KEY`).
3. Push your code and watch the workflows run.

---

This starter kit is not just about automation — it's about **thinking critically** about your workflow. Use these files as a foundation, and adapt them to your own needs.
