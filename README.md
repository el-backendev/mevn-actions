# MEVN Actions

A minimal MEVN stack (MongoDB, Express, Vue, Node.js) boilerplate with GitHub Actions CI/CD workflows.

## Project Structure

```
mevn-actions/
├── client/          # Vue 3 + Vite frontend
├── server/          # Express backend
├── .github/
│   └── workflows/   # CI/CD workflows
└── docs/            # Documentation
```

## Getting Started

### Prerequisites

- Node.js 20+
- npm 9+

### Installation

```bash
npm install
```

This will install dependencies for both `client/` and `server/`.

### Development

```bash
# Run frontend dev server
cd client && npm run dev

# Run backend dev server
cd server && npm run dev
```

### Testing

```bash
npm test
```

### Linting

```bash
npm run lint
```

### Build

```bash
npm run build
```

## Workflows

- **CI Pipeline** (`ci.yml`): Runs lint and tests on every push/PR.
- **Build Workflow** (`build.yml`): Compiles the Vue frontend.
- **Deploy Workflow** (`deploy.yml`): Template for deployments (manual trigger).
- **Security Workflow** (`security.yml`): Runs CodeQL analysis weekly.

## Environment Variables

Copy `server/.env.example` to `server/.env` and fill in the values.
