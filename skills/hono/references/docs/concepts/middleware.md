---
source: https://github.com/honojs/website/blob/main/docs/concepts/middleware.md
live: https://hono.dev/docs/concepts/middleware
upstream_commit: a597bd40c01dd00a2ec2d8afd550c1ffebd2f7f1
synced: 2026-04-18
---

<!-- Synced from https://github.com/honojs/website/blob/main/docs/concepts/middleware.md -->
<!-- For the latest version fetch: https://raw.githubusercontent.com/honojs/website/main/docs/concepts/middleware.md -->

# Middleware

We call the primitive that returns `Response` as "Handler".
"Middleware" is executed before and after the Handler and handles the `Request` and `Response`.
It's like an onion structure.

![](/images/onion.png)

For example, we can write the middleware to add the "X-Response-Time" header as follows.

```ts twoslash
import { Hono } from 'hono'
const app = new Hono()
// ---cut---
app.use(async (c, next) => {
  const start = performance.now()
  await next()
  const end = performance.now()
  c.res.headers.set('X-Response-Time', `${end - start}`)
})
```

With this simple method, we can write our own custom middleware and we can use the built-in or third party middleware.
