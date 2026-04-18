---
source: https://github.com/honojs/website/blob/main/docs/guides/helpers.md
live: https://hono.dev/docs/guides/helpers
upstream_commit: a597bd40c01dd00a2ec2d8afd550c1ffebd2f7f1
synced: 2026-04-18
---

<!-- Synced from https://github.com/honojs/website/blob/main/docs/guides/helpers.md -->
<!-- For the latest version fetch: https://raw.githubusercontent.com/honojs/website/main/docs/guides/helpers.md -->

# Helpers

Helpers are available to assist in developing your application. Unlike middleware, they don't act as handlers, but rather provide useful functions.

For instance, here's how to use the [Cookie helper](/docs/helpers/cookie):

```ts
import { getCookie, setCookie } from 'hono/cookie'

const app = new Hono()

app.get('/cookie', (c) => {
  const yummyCookie = getCookie(c, 'yummy_cookie')
  // ...
  setCookie(c, 'delicious_cookie', 'macha')
  //
})
```

## Available Helpers

- [Accepts](/docs/helpers/accepts)
- [Adapter](/docs/helpers/adapter)
- [Cookie](/docs/helpers/cookie)
- [css](/docs/helpers/css)
- [Dev](/docs/helpers/dev)
- [Factory](/docs/helpers/factory)
- [html](/docs/helpers/html)
- [JWT](/docs/helpers/jwt)
- [SSG](/docs/helpers/ssg)
- [Streaming](/docs/helpers/streaming)
- [Testing](/docs/helpers/testing)
- [WebSocket](/docs/helpers/websocket)
