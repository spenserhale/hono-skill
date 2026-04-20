---
source: https://github.com/honojs/create-hono
---

# create-hono — project scaffolder

[`create-hono`](https://github.com/honojs/create-hono) is the `npm create hono` command. It prompts the user for a target runtime, then pulls the matching template from [honojs/starter](starter.md) into a new directory.

## The canonical invocation

```sh
npm create hono@latest
# or, with a project name:
npm create hono@latest my-app
```

Every modern JS package manager has a create-alias that forwards to this:

| PM | Command |
|---|---|
| npm | `npm create hono@latest [dir]` |
| pnpm | `pnpm create hono@latest [dir]` |
| yarn | `yarn create hono [dir]` |
| bun | `bun create hono@latest [dir]` |
| deno | `deno init --npm hono [dir]` |

## Flags

> **Note:** When using `npm create`, flags must come after `--` to stop npm from consuming them. Other PMs pass flags through directly.

| Flag | Purpose |
|---|---|
| `-t, --template <name>` | Skip the interactive template prompt. Name must match a folder under [honojs/starter/templates](starter.md). |
| `-i, --install` | Install dependencies after scaffolding. Skips the "run install?" prompt. |
| `-p, --pm <pnpm\|bun\|deno\|npm\|yarn>` | Force a package manager for the install step. Otherwise auto-detected. |
| `-o, --offline` | Use a locally cached copy of the templates (useful in CI or flaky networks). |

## Examples

Create a Cloudflare Workers project and install deps with pnpm, no prompts:

```sh
npm create hono@latest ./my-app -- --template cloudflare-workers --install --pm pnpm
```

Same thing with pnpm directly (no `--`):

```sh
pnpm create hono@latest ./my-app --template cloudflare-workers --install
```

Scaffold a Bun project:

```sh
bun create hono@latest my-app --template bun --install
```

Scaffold a Deno project:

```sh
deno init --npm hono my-app -- --template deno
```

CI use (offline templates, no prompts):

```sh
npm create hono@latest my-app -- --template x-basic --install --pm npm --offline
```

## What it produces

The output directory contains the chosen template's contents — typically:

- `package.json` with Hono + a runtime adapter (`@hono/node-server`, `wrangler`, etc.)
- A `src/index.ts` (or `.tsx`) entry file with a minimal `new Hono().get('/', ...)` example
- A runtime-specific config (`wrangler.toml`, `vercel.json`, `deno.json`, etc.)
- A README pointing to [hono.dev](https://hono.dev)

After scaffolding, the per-runtime getting-started page is the right next read — e.g. `references/docs/getting-started/cloudflare-workers.md`.

## Gotchas

- **Template names are exact** — they must match the folder name in honojs/starter. Typos silently fall back to the interactive picker.
- **`--offline` requires a prior non-offline run** in the same install location to populate the cache.
- **`yarn create hono` does not take `@latest`** — yarn classic resolves to the latest automatically.

## Getting fresh information

Check the upstream README or run `npm create hono@latest -- --help`:

```sh
npm create hono@latest -- --help
curl -fsSL https://raw.githubusercontent.com/honojs/create-hono/main/README.md
```
