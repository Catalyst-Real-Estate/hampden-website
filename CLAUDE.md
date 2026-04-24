# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML website for the Hampden property. Hosted on GitHub Pages. No build tools or frameworks; everything is vanilla HTML5, CSS3, and JavaScript.

## Where to make changes

- **Content edits** (copy, images, floor plans, listings) → edit `index.html` and the `images/` directory in this repo directly.
- **Workflow, CI, or shared-convention edits** (validate rules, Pages config, sync logic) → do NOT edit the workflow files here; open a PR against [`property-site-theme`](https://github.com/Catalyst-Real-Estate/property-site-theme) instead. Those changes will propagate back to this repo via the daily sync PR opened by `sync-from-theme.yml`.
- **Never force-merge** a sync PR if `validate.yml` fails on it. Fix the underlying issue in the theme repo first.

## Validation

HTML is validated via HTMLHint in CI. To validate locally:

```bash
npm install -g htmlhint
htmlhint "**/*.html"
```

CI runs automatically on push/PR to `main` via `.github/workflows/validate.yml`.

## Deployment

Pushing to `main` automatically deploys via GitHub Pages. No manual deploy step. The `.nojekyll` file disables Jekyll processing so HTML is served as-is.

## Architecture

Planned: single-file `index.html` following the same pattern as `lynn-park-website` — all CSS in one `<style>` block, all JS in one `<script>` block at the bottom, no external JS/CSS files, no build.

Expected sections (to mirror lynn-park once content is ready):
1. Sticky `<nav>` header
2. Hero with image carousel
3. Available Spaces / unit listings
4. Gallery
5. Features, About, Location, FAQ
6. CTA banner and footer

Per-property assets live in `images/`. Floor plans, slider images, gallery photos follow the same naming conventions as lynn-park.

## Files inherited from theme

These are kept in sync automatically — do not edit in this repo:

- `.github/workflows/validate.yml`
- `.github/workflows/pages.yml`
- `.github/workflows/sync-from-theme.yml`
- `.gitignore`
- `.nojekyll`

`.templatesyncignore` controls what the daily sync leaves alone — adjust carefully if you need per-property overrides.
