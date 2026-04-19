# hono skill

An agent skill (SKILL.md format) containing the whole [Hono](https://hono.dev) ecosystem as offline reference material — all 84 official docs pages, plus guides for the starter template, `create-hono`, and official example apps.

## What's inside

```
skills/hono/
├── SKILL.md                        ← index; entry point for the AI
├── references/
│   ├── starter.md                  ← honojs/starter templates
│   ├── create-hono.md              ← create-hono CLI
│   ├── examples.md                 ← honojs/examples apps
│   └── docs/                       ← synced from honojs/website
│       ├── _manifest.md            ← upstream commit + sync date
│       ├── api/                    ← Hono, Context, Request, Routing, etc.
│       ├── concepts/               ← motivation, routers, benchmarks
│       ├── getting-started/        ← one file per runtime target
│       ├── guides/                 ← RPC, validation, testing, JSX, …
│       ├── helpers/                ← cookie, jwt, streaming, websocket, …
│       └── middleware/builtin/     ← cors, jwt, auth, cache, etag, …
└── scripts/
    └── sync-docs.sh                ← regenerates references/docs/

.github/workflows/sync-docs.yml     ← weekly automated sync PR
```

Every file under `references/` carries YAML frontmatter with the upstream `source:` GitHub URL, the live `live:` hono.dev URL, and the `synced:` date — so an agent using this skill can decide when to fetch the latest version instead of relying on the snapshot.

## Installing the skill

Drop it into your agent's skills directory. Example for Claude Code:

```sh
# copy just the skill folder
cp -r skills/hono ~/.claude/skills/

# or clone this whole repo
git clone https://github.com/spenserhale/hono-skill ~/.claude/skills/hono-skill
```

Then reload your agent so it picks up the new skill.

Other agent runtimes that understand the SKILL.md format should work the same way — point them at `skills/hono/`.

## Keeping it in sync

A [GitHub Action](.github/workflows/sync-docs.yml) runs weekly and opens a PR when upstream docs change. You can also run it manually:

```sh
# Regenerate references/docs/ from the latest honojs/website main
bash skills/hono/scripts/sync-docs.sh

# Or pin to a specific upstream ref (branch, tag, or SHA)
bash skills/hono/scripts/sync-docs.sh --ref v4.6.0
```

The script:

1. Clones [honojs/website](https://github.com/honojs/website) shallowly to a temp dir.
2. Walks `docs/**/*.md`, preserving the directory structure into `references/docs/`.
3. Prepends YAML frontmatter with the upstream source URL, live hono.dev URL, upstream commit SHA, and sync date.
4. Strips VitePress-specific `:::` container fences (tip/info/warning/danger become blockquote headers; code-group / details wrappers are dropped and the inner code fences stand on their own).
5. Writes a `_manifest.md` recording the upstream commit.

## Related

- Upstream docs: https://github.com/honojs/website · https://hono.dev
- Companion skill (CLI): https://github.com/spenserhale/hono-cli-skill
