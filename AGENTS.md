# AGENTS.md

## Architecture

Static, framework-free two-page site. No bundler, no `package.json`, no build command — Netlify serves the HTML files directly.

- `index.html` — home page (hero, about, solutions grid, contact form, footer).
- `essentials.html` — served at `/essentials` via Netlify's default pretty-URL behavior (the `.html` extension is stripped automatically).
- `netlify.toml` — sets `publish = "."` and adds baseline security headers.

## Conventions

- Styling is Tailwind utility classes via the CDN script tag (`<script src="https://cdn.tailwindcss.com">`), plus a small `<style>` block per page for hover states and animations that Tailwind's default utilities don't express cleanly (e.g. `.process-box:hover`, `.fav-card:hover`).
- Both pages duplicate the nav/header/footer markup rather than sharing a component — there's no templating layer, so this is intentional, not an oversight. Keep nav links and footer contact info in sync across both files when editing either.
- Brand color is `#3B0B45` (deep purple), referenced directly via Tailwind arbitrary-value classes (`text-[#3B0B45]`, `bg-[#3B0B45]`) rather than a Tailwind config extension, since there is no Tailwind config file with the CDN build.
- Dark mode uses Tailwind's default `dark:` variant (`prefers-color-scheme` media query) — no manual toggle.

## Contact form

The inquiry form on the home page (`#custom-sandra-form`) submits via Netlify Forms AJAX (`fetch('/', ...)` with `application/x-www-form-urlencoded` body). It replaced an earlier version of this page that posted to a third-party webhook placeholder — that URL was never filled in, so submissions went nowhere. If Sandra wants leads routed into a CRM (e.g. GoHighLevel/Pipeline Pro) instead of just the Netlify Forms inbox, add a `netlify/functions/submission-created.mts` function per the `netlify-forms` skill to forward each submission on.

## Essentials page filtering

`essentials.html` filters/searches purely client-side over the `data-category` and `data-name` attributes on each `.fav-card`. Adding a new recommended tool means adding a new `.fav-card` block and, if it's a new category, a new filter button in the `filterItems()` button row.

No roadmap document is needed — this site is complete as delivered.
