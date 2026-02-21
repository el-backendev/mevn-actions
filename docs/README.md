# MEVN Actions Starter Kit

This repository provides a set of GitHub Actions workflows tailored for the MEVN stack (MongoDB, Express, Vue, Node.js).

## Why choose Actions for your workflow?

- **Automation**: Save time by letting GitHub handle repetitive tasks.
- **Consistency**: Ensure every build, test, and deploy follows the same rules.
- **Confidence**: Catch bugs and vulnerabilities before they reach production.

## Included Workflows

All workflows have been optimized with modern GitHub Actions best practices:

- **CI Pipeline**: Runs ESLint with automated PR comments and tests with coverage on Node 18, 20, 22
- **Build Workflow**: Compiles the Vue frontend with caching, validation, and artifact uploads
- **Deploy Workflow**: Deploys to GitHub Pages, Heroku, and Render with build artifact reuse
- **Security Workflow**: 4-layer security analysis (CodeQL, Snyk, npm audit, OpenSSF Scorecard)

## Brainstorming Questions

- Why is CI important for small teams as well as large ones?
- When should you trigger deploys automatically, and when should you hold them back?
- How can security scans be integrated without slowing down development?
- What happens if you skip automation entirely?
- Should builds run on every branch, or only on main?
- Is deploying every commit sustainable, or should you prefer tagged releases?

## Getting Started

1. Copy the workflows into your project's `.github/workflows` directory.
2. Configure required secrets and variables (see [Configuration Guide](CONFIGURATION.md)).
3. Push your code and watch the optimized workflows run.

For detailed configuration instructions, troubleshooting, and customization options, see the **[Configuration Guide](CONFIGURATION.md)**.

---

This starter kit is not just about automation — it's about **thinking critically** about your workflow. Use these files as a foundation, and adapt them to your own needs.
