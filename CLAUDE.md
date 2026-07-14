# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static one-page marketing site for "Sistemas BBD" (plain HTML + CSS + JS, no build step, no framework, no package manager). Sections: Home, Nosotros, Valores, Contacto, all on a single continuous-scroll `index.html`.

## Structure

- `index.html` — entire page content/markup
- `css/styles.css` — all styling
- `js/main.js` — mobile nav toggle, marquee duplication for seamless CSS loop, and scroll-reveal via IntersectionObserver
- `img/` — static assets

## Local development

No build/lint/test tooling exists. Serve the folder with any static file server and open it in a browser, e.g.:

```
npx serve .
```

or Python's `http.server`. Then visit the printed localhost URL.

## Contact / WhatsApp integration

Contact is exclusively via WhatsApp links (`https://wa.me/<number>`) embedded directly in `index.html`, with a preloaded message. When updating the phone number or message, edit these links directly in `index.html` — there is no config file for this.

## Deployment

Deployment is automatic via `.github/workflows/deploy.yml`: on every push to `main`, the workflow rsyncs the repo contents (excluding `.git*`, `.github`, `README.md`) to the production server at `/srv/sites/bbdsistemas/html/` over SSH, using secrets `SSH_HOST`, `SSH_USER`, and `SSH_PRIVATE_KEY`. There is no staging environment — pushing to `main` deploys straight to production.
