# Liquid Glass UI v0.2

Production-oriented Liquid Glass UI library.

The project is intentionally **CSS-first and WebGL-optional**.

It is designed to be deployed as a public static package/site on Cloudflare while keeping a Worker available for routing, metadata and KV-backed configuration.

## Quick start

```bash
npm install @liquid-glass/ui
```

```html
<link rel="stylesheet" href="liquid-glass.css">

<section class="lg-glass lg-card" data-liquid-glass>
  <h2>Liquid Glass</h2>
  <p>Your semantic content stays ordinary HTML.</p>
</section>
```

```js
import { enhanceGlass } from "@liquid-glass/ui";
enhanceGlass();
```

## Design philosophy

This is a library, not a screenshot recreation.

```text
HTML
 │
 ├── CSS material ─────────────── always available
 │
 └── WebGL optical ────────────── optional enhancement
```

A missing GPU feature must never turn a usable component into a broken component.

## What is included

- CSS Liquid Glass material
- pointer-aware optical highlight
- backdrop-filter fallback
- WebGL shared optical renderer
- capability detection
- device performance profile
- stress-test example
- user-facing documentation
- Cloudflare Worker + KV skeleton
- Agent Skill specification

## Stress Lab

Open:

```text
examples/stress-test.html
```

It intentionally exercises multiple surfaces, dynamic insertion, pointer interaction, controls and performance telemetry.

This is the page to use while tuning the library.

## Cloudflare

The library is static. A Worker should not sit between every shader or CSS asset request.

Recommended architecture:

```text
Cloudflare Edge
      │
      ├── /dist/*       immutable static assets
      ├── /examples/*   demos
      ├── /docs/*       documentation
      │
      └── /api/*
            │
          Worker
            │
            └── KV
```

See `worker/`.

## License

MIT.
