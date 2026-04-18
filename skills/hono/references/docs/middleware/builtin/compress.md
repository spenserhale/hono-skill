---
source: https://github.com/honojs/website/blob/main/docs/middleware/builtin/compress.md
live: https://hono.dev/docs/middleware/builtin/compress
upstream_commit: a597bd40c01dd00a2ec2d8afd550c1ffebd2f7f1
synced: 2026-04-18
---

<!-- Synced from https://github.com/honojs/website/blob/main/docs/middleware/builtin/compress.md -->
<!-- For the latest version fetch: https://raw.githubusercontent.com/honojs/website/main/docs/middleware/builtin/compress.md -->

# Compress Middleware

This middleware compresses the response body, according to `Accept-Encoding` request header.

> **Info**
**Note**: On Cloudflare Workers and Deno Deploy, the response body will be compressed automatically, so there is no need to use this middleware.

## Import

```ts
import { Hono } from 'hono'
import { compress } from 'hono/compress'
```

## Usage

```ts
const app = new Hono()

app.use(compress())
```

## Options

### <Badge type="info" text="optional" /> encoding: `'gzip'` | `'deflate'`

The compression scheme to allow for response compression. Either `gzip` or `deflate`. If not defined, both are allowed and will be used based on the `Accept-Encoding` header. `gzip` is prioritized if this option is not provided and the client provides both in the `Accept-Encoding` header.

### <Badge type="info" text="optional" /> threshold: `number`

The minimum size in bytes to compress. Defaults to 1024 bytes.
