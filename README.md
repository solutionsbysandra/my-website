# Solutions by Sandra

A two-page marketing site for Sandra's business-systems consulting practice. She helps founders set up sales funnels, CRM automations, and back-office systems, and this site is her home base for attracting and capturing new client inquiries.

## Pages

- **Home** (`index.html`) — hero, "how I help" process steps, a grid of service offerings, and a contact form.
- **Essentials** (`essentials.html`) — a searchable, filterable directory of tools and affiliate resources Sandra recommends, grouped by category (Finance, Tech, Rewards, Support).

## Technology

- Plain HTML with [Tailwind CSS](https://tailwindcss.com) loaded via CDN — no build step required.
- [Font Awesome](https://fontawesome.com) for icons.
- The contact form is powered by [Netlify Forms](https://docs.netlify.com/forms/setup/), submitted via AJAX so visitors get an inline "thank you" state without leaving the page.

## Running locally

No install or build step is needed — this is a static site. From the project root:

```bash
netlify dev
```

This serves the site (with Netlify Forms emulation) at the printed local URL.

## Deploying

The site deploys as-is; `netlify.toml` sets the publish directory to the project root. Form submissions appear in the Netlify UI under **Forms** once deployed.
