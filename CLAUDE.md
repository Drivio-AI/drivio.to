# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static marketing site for the Drivio iOS app, served from the repo root on GitHub Pages. The custom domain `drivio.to` is configured via the `CNAME` file — any push to `main` deploys live.

There is no build step, no package manager, no test suite, and no JS framework. Each page is a single self-contained `.html` file with inline `<style>` and a tiny inline `<script>`.

## Pages

- `index.html` — landing page (hero, features, how-it-works, pricing, CTA)
- `privacy.html` — privacy policy
- `terms.html` — terms of service
- `support.html` — App Store support URL (contact + FAQ)

## Local preview

Open the file directly in a browser, or serve the directory:

```
python3 -m http.server 8000
```

## Styling conventions

`index.html` defines its design system in CSS custom properties on `:root` (top of `<style>`): `--bg` (#0F2C3E navy), `--accent` (#C55A40 terracotta), `--cream` (#F5EEE0), plus card/text/border tokens. **Reuse these variables rather than hardcoding hex values when editing index.html.**

`privacy.html` and `terms.html` were authored separately and use a different palette (`--bg: #0B1A2E`, `--accent: #F0833D`) — they are intentionally not unified with index.html. Don't "fix" the divergence unless asked.

Animations on the landing page rely on a `.fade-up` class observed by an `IntersectionObserver` at the bottom of `index.html`. New scroll-revealed sections need that class to animate in.

## Assets

Icons (`favicon-*.png`, `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`) and `logo.png` are referenced by relative path from each HTML file. `logo2.png` is gitignored (kept locally as a working file).
