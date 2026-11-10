# Development setup

Applies to `urbiva-app`. Commands are taken from its `package.json`.

## Requirements

- Node.js 20.9 or newer (CI uses Node 22)
- npm

## Steps

```bash
git clone https://github.com/urbiva/urbiva-app.git
cd urbiva-app
npm install
cp .env.example .env.local     # optional: ANTHROPIC_API_KEY for live AI
npm run dev                     # http://localhost:3000
```

## Checks

```bash
npm run typecheck   # tsc --noEmit
npm test            # tsx --test tests/*.test.ts
npm run build       # prebuild fetches and verifies fonts, then next build
npm run verify      # all of the above
```

CI (`.github/workflows/ci.yml`) runs install, type check, tests and build on every push and pull request to `main`. It has read-only permissions, uses no secrets and never deploys.

## Branches

`feat/*`, `fix/*`, `docs/*`, `chore/*` into `main` through pull requests.
