---
source: https://github.com/honojs/website/blob/main/docs/concepts/motivation.md
live: https://hono.dev/docs/concepts/motivation
upstream_commit: a597bd40c01dd00a2ec2d8afd550c1ffebd2f7f1
synced: 2026-04-18
---

<!-- Synced from https://github.com/honojs/website/blob/main/docs/concepts/motivation.md -->
<!-- For the latest version fetch: https://raw.githubusercontent.com/honojs/website/main/docs/concepts/motivation.md -->

# Philosophy

In this section, we talk about the concept, or philosophy, of Hono.

## Motivation

At first, I just wanted to create a web application on Cloudflare Workers.
But, there was no good framework that works on Cloudflare Workers.
So, I started building Hono.

I thought it would be a good opportunity to learn how to build a router using Trie trees.
Then a friend showed up with ultra crazy fast router called "RegExpRouter".
And I also have a friend who created the Basic authentication middleware.

Using only Web Standard APIs, we could make it work on Deno and Bun. When people asked "is there Express for Bun?", we could answer, "no, but there is Hono".
(Although Express works on Bun now.)

We also have friends who make GraphQL servers, Firebase authentication, and Sentry middleware.
And, we also have a Node.js adapter.
An ecosystem has sprung up.

In other words, Hono is damn fast, makes a lot of things possible, and works anywhere.
We might imagine that Hono could become the **Standard for Web Standards**.
