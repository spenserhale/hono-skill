---
name: hono
description: Offline reference for the Hono web framework — all 84 docs pages (routing, API, middleware, helpers, RPC, JSX, validation, testing, per-runtime getting-started), plus starter templates, the `create-hono` scaffolder, and example apps. Use for anything Hono: routes, middleware, helpers, deploying to Workers/Pages/Bun/Deno/Node/Vercel/Lambda/etc., the `hc` RPC client, JSX/SSR, or Zod/Valibot/ArkType validation — even if "Hono" isn't named (code imports `hono` or `@hono/*`). For `hono` CLI commands, defer to the `hono-cli` skill.
---

# Hono skill — index

Hono is a small, fast, web-standards-based framework that runs on every modern JavaScript runtime. This skill is your offline reference to the whole ecosystem.

> **Every reference file in this skill carries `source:` and `live:` frontmatter pointing to the upstream GitHub file and the hono.dev page it was generated from.** If anything looks stale or you need the absolute latest, fetch the raw file from GitHub (the URL is in each file's header comment) instead of guessing.

## What lives where

| Area | Where to look | Upstream |
|---|---|---|
| Full docs (routing, API, middleware, helpers, guides, concepts, per-runtime getting-started) | [`references/docs/`](references/docs/) — mirrors hono.dev/docs | [honojs/website](https://github.com/honojs/website) |
| Starter template repo (templates consumed by `create-hono`) | [`references/starter.md`](references/starter.md) | [honojs/starter](https://github.com/honojs/starter) |
| `create-hono` scaffolder (`npm create hono@latest`) | [`references/create-hono.md`](references/create-hono.md) | [honojs/create-hono](https://github.com/honojs/create-hono) |
| Official example apps | [`references/examples.md`](references/examples.md) | [honojs/examples](https://github.com/honojs/examples) |

For CLI-related tasks (`hono docs`, `hono serve`, etc.) see the separate [`hono-cli`](https://github.com/honojs/cli) skill.

## How to use this skill

Pick the shallowest reference that answers the question. The docs tree is pre-organized by hono.dev's own sidebar, so your instinct from the public site transfers directly.

**Scaffolding a new project** → [`references/create-hono.md`](references/create-hono.md), then the matching per-runtime getting-started page under [`references/docs/getting-started/`](references/docs/getting-started/).

**Deploying / choosing a runtime** → `references/docs/getting-started/<runtime>.md`. One file per target: `cloudflare-workers`, `cloudflare-pages`, `bun`, `deno`, `nodejs`, `vercel`, `netlify`, `aws-lambda`, `lambda-edge`, `fastly`, `azure-functions`, `google-cloud-run`, `supabase-functions`, `ali-function-compute`, `service-worker`, `webassembly-wasi`, `nextjs`.

**Core API** → [`references/docs/api/`](references/docs/api/):
- `hono.md` — the `Hono` app class, routing methods, `.route()`, `.basePath()`
- `routing.md` — path params, regex, chained routes
- `request.md` — `c.req.*` (params, query, body parsing)
- `context.md` — `c.*` (`c.json`, `c.text`, `c.html`, `c.redirect`, `c.env`, `c.get/c.set`, `c.executionCtx`)
- `exception.md` — `HTTPException`
- `presets.md` — `hono/tiny`, `hono/quick`, regex vs trie routers

**Middleware** → [`references/docs/middleware/builtin/`](references/docs/middleware/builtin/). One file per built-in:
`basic-auth`, `bearer-auth`, `jwt`, `jwk`, `cors`, `csrf`, `secure-headers`, `logger`, `timing`, `request-id`, `context-storage`, `cache`, `compress`, `etag`, `body-limit`, `method-override`, `trailing-slash`, `ip-restriction`, `jsx-renderer`, `pretty-json`, `timeout`, `language`, `combine`.

**Helpers** → [`references/docs/helpers/`](references/docs/helpers/): `cookie`, `jwt`, `css`, `html`, `streaming`, `ssg`, `websocket`, `testing`, `dev`, `factory`, `adapter`, `proxy`, `route`, `accepts`, `conninfo`.

**Guides (big-picture patterns)** → [`references/docs/guides/`](references/docs/guides/): `best-practices`, `validation`, `rpc`, `testing`, `jsx`, `jsx-dom`, `middleware`, `helpers`, `examples`, `create-hono`, `faq`, `others`.

**Concepts (why & how it's built)** → [`references/docs/concepts/`](references/docs/concepts/): `motivation`, `routers`, `benchmarks`, `middleware`, `web-standard`, `developer-experience`, `stacks`.

## Workflow: answering a Hono question

1. **Narrow to an area** using the table above.
2. **Open the matching file** under `references/`. Read the frontmatter — it tells you the upstream path and sync date.
3. **If the sync date is old** or the user reports behavior that doesn't match: fetch the latest with the URL in the file's header comment (or `curl -fsSL <raw_url>`) and trust that instead.
4. **Cross-reference**: middleware pages assume the Context API; helper pages assume familiarity with routes. When a file references `c.json()` or similar without defining it, look in [`references/docs/api/context.md`](references/docs/api/context.md).

## When to prefer live sources

The docs here are a snapshot. Prefer fetching live when:

- The user reports behavior that conflicts with this reference (framework may have updated).
- The user asks about a middleware/helper/runtime that isn't in the tree (may be new upstream).
- The `synced:` date in the relevant file is more than a few weeks old and the user is shipping production code.
- The user is on a Hono version newer than the snapshot implies (check their `package.json`).

Each doc file's frontmatter has the `source:` GitHub URL. The raw file for `curl`/WebFetch is the same URL with `github.com/…/blob/` swapped for `raw.githubusercontent.com/…/`.

## Staying in sync

This skill is refreshed from upstream via:

- `scripts/sync-docs.sh` — clones honojs/website, converts VitePress markdown to skill reference files, embeds provenance frontmatter.
- `.github/workflows/sync-docs.yml` — runs the script on a schedule (and on demand) and commits the result.

`references/docs/_manifest.md` records the upstream commit SHA of the last sync.
