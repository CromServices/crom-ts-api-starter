<!--
README TEMPLATE. When you reuse this starter, keep the six sections below and
fill in the parts marked with angle brackets. Keep it public-safe: no personal
names, no internal pricing or sales notes, location "Australia" only.
-->

# crom-ts-api-starter

<!-- Set to the same name/description as package.json "starter.config". -->
Express + TypeScript API starter: `/health`, request validation, a `Store<T>` interface, tests, Docker and Fly config.

## What it is

A small, strict TypeScript API built on Express, ready to copy for a new job.

- `GET /health` returns `{"status":"ok"}`.
- `GET /` serves a minimal HTML page (unstyled; picks up the shared theme when it is live).
- `GET|POST /items`, `GET|DELETE /items/:id`: an **example** resource that shows request validation and the store wired together. Rename or delete it.
- `src/lib/validate.ts`: a tiny validation helper (`requireString`, `isPlainObject`) and a `validateBody()` middleware that replies `400 {"error": ...}`.
- `src/store/store.ts`: the `Store<T>` interface. `src/store/memory.ts`: the in-memory implementation. Swap in a database adapter without touching the routes.
- Tests with `node:test` (run through `tsx`), a multi-stage `Dockerfile`, and `fly.toml`.

| Path | Purpose |
|---|---|
| `src/app.ts` | `createApp()`: routes and middleware |
| `src/server.ts` | Listen entry (`PORT`, `HOST`) |
| `src/config.ts` | Reads `starter.config` from `package.json` |
| `src/lib/validate.ts` | Validation helper |
| `src/store/` | `Store<T>` + `InMemoryStore<T>` |
| `src/routes/items.ts` | Example resource |
| `test/` | `node:test` suites |

## What it proves

<!-- Per project: one or two lines on what this repo shows a client. -->
- A typed API with validation, a swappable storage layer and tests, set up the same way every time.
- One command to build a production image; the same health check locally and on the host.

## Live link

<!-- Per project: replace with the deployed URL, or keep "Not hosted". -->
Not hosted. This is the template; each project sets its own app and adds the link here.

## Run in 3 commands

Needs Node 20 or newer.

```bash
npm install
npm test
npm run dev        # http://localhost:3000/health
```

`npm run build` compiles to `dist/`, and `npm start` runs the compiled server. Copy `.env.example` to `.env` to change `PORT` or `HOST`.

## Reuse for a new job

1. **Use this template.** On GitHub, click **Use this template** to create the project repo.
2. **Set the name.** In `package.json`, update `name` and the `starter.config` block (`name`, `description`, `liveUrl`), then update the title and description at the top of this README to match. Leave `source` as is and set `ref` to the starter commit you started from, so later drift is one diff away.
3. **Set the app name.** In `fly.toml`, replace `crom-CHANGE-ME` with the project's Fly app name.
4. **Build the API.** Replace the example `items` route (and `test/app.test.ts` cases) with the job's routes. Keep `Store<T>` and add an adapter if it needs a database.
5. **Deploy.** With a Fly token on hand: `fly apps create <app-name>` once, then `fly deploy`. Put the URL in **Live link**.

<!-- CI: reusable CI and deploy workflows will be added as thin callers once the shared workflows are released. -->

## Footer

<!-- CROM THEME SLOT: replace with crom-shared README.template.md footer when live -->
Built by [Crom Services, Australia](https://cromservices.com.au)

MIT licence, see [LICENSE](LICENSE).
