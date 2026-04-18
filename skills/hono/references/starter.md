---
source: https://github.com/honojs/starter
live: https://github.com/honojs/starter
synced: 2026-04-18
---

<!-- Synced from https://github.com/honojs/starter -->
<!-- For the latest version fetch: https://raw.githubusercontent.com/honojs/starter/main/README.md -->

# honojs/starter — starter templates

[`honojs/starter`](https://github.com/honojs/starter) is the template source repo consumed by [`create-hono`](create-hono.md). Users don't clone it directly — they run `npm create hono@latest` and pick a template.

If a user asks "what templates exist?" or "what runtimes does `create-hono` support?", this is the authoritative list.

## Available templates

Templates live under `/templates/<name>/` in the upstream repo. Names match what `create-hono` accepts as `--template <name>`.

| Template | Target runtime / platform |
|---|---|
| `aws-lambda` | AWS Lambda (Node runtime, API Gateway / Function URL) |
| `bun` | Bun standalone |
| `cloudflare-pages` | Cloudflare Pages (Functions) |
| `cloudflare-workers` | Cloudflare Workers (Wrangler, no Vite) |
| `cloudflare-workers+vite` | Cloudflare Workers with Vite dev server |
| `deno` | Deno (`Deno.serve`) |
| `fastly` | Fastly Compute |
| `lambda-edge` | AWS Lambda@Edge (CloudFront) |
| `netlify` | Netlify Edge Functions |
| `nextjs` | Next.js (Route Handlers) |
| `nodejs` | Node.js (`@hono/node-server`) |
| `vercel` | Vercel Edge / Node |
| `x-basic` | Framework-agnostic minimal template (runtime-neutral) |

## Picking the right one

- **New user, unsure** → `cloudflare-workers` is the reference runtime for Hono; the team uses it in most docs examples.
- **Wants a local long-lived server** → `nodejs` or `bun`.
- **Wants Vite HMR on Workers** → `cloudflare-workers+vite` (distinct from plain `cloudflare-workers`).
- **Starting from nothing, no runtime opinion yet** → `x-basic`.
- **Already using another framework** → `nextjs` (Route Handlers), or `vercel`/`netlify`/`cloudflare-pages` when pairing with a marketing/front-end site.

## Using a template

Always via `create-hono`:

```sh
npm create hono@latest my-app -- --template cloudflare-workers
pnpm create hono@latest my-app --template bun
bun create hono@latest my-app --template nodejs
```

See [`create-hono.md`](create-hono.md) for all flags.

## Getting fresh information

Templates occasionally get added or updated. To check the current set:

```sh
# List templates without cloning
curl -fsSL https://api.github.com/repos/honojs/starter/contents/templates | jq -r '.[].name'
```

Or visit [github.com/honojs/starter/tree/main/templates](https://github.com/honojs/starter/tree/main/templates).
