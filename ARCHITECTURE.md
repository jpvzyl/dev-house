# dev-house — Architecture

## Purpose
A software-agency ("dev house") website built with Astro and served by a small Express
server — a content/marketing site with TypeScript, a `src/` content tree, and a build to
`dist/`.

## Tech stack
| Layer | Choice | Where |
|---|---|---|
| Site framework | **Astro** | `astro.config.mjs`, `src/` |
| Language | **TypeScript** | `tsconfig.json`, `src/` |
| Server | **Express** (`node server.js`) | `server.js` |
| Build output | `dist/` | repo |
| Hosting | Heroku-style (`Procfile`) | repo |

## Repository / program layout
```
dev-house/
├── astro.config.mjs       # Astro config
├── src/                   # Astro pages/components/content
├── public/                # static assets
├── server.js              # Express server (serves built site)
├── dist/                  # build output
├── notes/                 # working notes
├── package.json  tsconfig.json  Procfile
```

## Programs / services / apps
- **Astro site (`src/`)** — the marketing/content website (static-first, component-based).
- **Express server (`server.js`)** — serves the built Astro output in production.

## Architecture & data flow
```
Browser ─▶ Express (server.js) ─▶ Astro-built static site (dist/)
```
Static-first content site; Astro renders pages at build time, Express serves them. No backend
API/DB observed.

## Integrations / external services
Heroku hosting. None beyond static content observed.

## Deployment
`Procfile` + `node server.js` (Heroku); Astro build → `dist/`.

## Notable features & sharp edges
- Astro is the odd-one-out toolchain in this portfolio (most other sites are Vite/React or
  Rails) — different build model to maintain.
- Pure presentation layer; nothing security/data-sensitive here.
