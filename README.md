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

## Halloween CSS add-on

A reusable, CSS-only seasonal accent is available at `styles/halloween.css`.
It adds small fixed pumpkin/ghost decorations and optional glass-card styles.
It does not require JavaScript, external images, fonts, or network requests beyond loading the stylesheet.

Load it from jsDelivr:

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/gh/KyuuCharlie/liquid-glass-ui@main/styles/halloween.css"
>
```

The decorative accents appear automatically when the stylesheet is loaded. To use the optional card treatment, add `lg-halloween-card` to a component; use `lg-halloween-accent` for accent text. The decorations ignore pointer events and respect `prefers-reduced-motion`.

## License

GPL v3.
