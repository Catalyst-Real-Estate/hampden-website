# Hampden Website

Static website for the Hampden property. Hosted on GitHub Pages.

## Structure

Everything lives in this one repo. Shared conventions (workflows, tooling, CLAUDE.md baseline) are inherited from [`property-site-theme`](https://github.com/Catalyst-Real-Estate/property-site-theme) via `actions-template-sync`. Per-property files — `index.html`, `images/`, `CNAME`, this README — are kept here and excluded from sync via `.templatesyncignore`.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

No build step. Vanilla HTML/CSS/JS. `.nojekyll` disables Jekyll on GitHub Pages so files are served as-is.

## Workflows

- `validate.yml` — HTMLHint on every push/PR.
- `pages.yml` — deploys to GitHub Pages on push to `main`.
- `sync-from-theme.yml` — daily PR syncing shared conventions from `property-site-theme`; never force-merge if validation fails.

See `CLAUDE.md` for detailed guidance when editing this site.

## Status

Placeholder site — real content pending floor plans and photography.
