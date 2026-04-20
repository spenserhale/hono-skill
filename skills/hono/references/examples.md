---
source: https://github.com/honojs/examples
---

# honojs/examples — runnable example apps

[`honojs/examples`](https://github.com/honojs/examples) is a monorepo of small, self-contained Hono apps that demonstrate concrete patterns. Use it as a "show me, don't tell me" companion to the docs.

When a user asks "how would I actually structure X in Hono?", pointing at an example is often higher-signal than walking through docs.

## Running any example

Clone and work from a single workspace:

```sh
git clone https://github.com/honojs/examples
cd examples
npm install
npm -w <workspace-name> run dev
```

Deno and Bun examples have their own commands (see each example's README).

To read an example without cloning:

```sh
# Browse structure
gh api repos/honojs/examples/contents/<example-name>
# Or raw-fetch a specific file
curl -fsSL https://raw.githubusercontent.com/honojs/examples/main/<example-name>/src/index.ts
```

## Examples

| Name | What it shows | Runtime |
|---|---|---|
| [`basic`](https://github.com/honojs/examples/tree/main/basic) | Minimal Hono app, starting point | Any |
| [`blog`](https://github.com/honojs/examples/tree/main/blog) | CRUD with routing, validation, persistence patterns | Cloudflare Workers |
| [`bun`](https://github.com/honojs/examples/tree/main/bun) | Bun-specific conventions | Bun |
| [`deno`](https://github.com/honojs/examples/tree/main/deno) | Deno-specific conventions | Deno |
| [`durable-objects`](https://github.com/honojs/examples/tree/main/durable-objects) | Cloudflare Durable Objects with Hono | Cloudflare Workers |
| [`env-vars`](https://github.com/honojs/examples/tree/main/env-vars) | Typed Bindings / Variables via `new Hono<{ Bindings; Variables }>()` | Cloudflare Workers |
| [`hono-vite-jsx`](https://github.com/honojs/examples/tree/main/hono-vite-jsx) | `hono/jsx/dom` client-side, Vite dev server | Any + Vite |
| [`jsx-ssr`](https://github.com/honojs/examples/tree/main/jsx-ssr) | Server-rendered JSX pages | Any |
| [`nextjs-stack`](https://github.com/honojs/examples/tree/main/nextjs-stack) | Hono mounted in a Next.js Route Handler | Next.js |
| [`pages-stack`](https://github.com/honojs/examples/tree/main/pages-stack) | Full Hono stack: Zod + zValidator + `hc` RPC + React on CF Pages | Cloudflare Pages |
| [`serve-static`](https://github.com/honojs/examples/tree/main/serve-static) | Static file serving across runtimes | Multiple |
| [`stytch-auth`](https://github.com/honojs/examples/tree/main/stytch-auth) | TODO app with Stytch auth, Workers, Vite | Cloudflare Workers + Vite |

## Which example to point at

- **"Give me a small real app"** → `blog`.
- **"I want end-to-end type-safe client + server"** → `pages-stack` (the `hc` RPC client is the star).
- **"How do I type `env`?"** → `env-vars`.
- **"Stateful / long-lived storage on Workers?"** → `durable-objects`.
- **"I'm using Next.js, how does Hono fit in?"** → `nextjs-stack`.
- **"SPA with Hono serving the API"** → `hono-vite-jsx` or `stytch-auth`.
- **"SSR without a framework"** → `jsx-ssr`.
- **"Just show me Hono in Bun/Deno"** → `bun` or `deno`.

## Gotchas

- The upstream README may lag the actual file tree (e.g. `nextjs-stack` existed on disk before it was listed). Trust `gh api repos/honojs/examples/contents/` over the README for the canonical list.
- Each example pins its own Hono version in `package.json`. When borrowing patterns, check the pinned version — older examples may use pre-`hc` or pre-Zod-validator APIs.

## Getting fresh information

```sh
# List current examples
gh api repos/honojs/examples/contents/ --jq '.[] | select(.type=="dir") | .name'

# Read an example's README
gh api repos/honojs/examples/contents/<name>/README.md --jq .content | base64 -d
```
