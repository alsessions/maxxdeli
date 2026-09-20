# Maxx Deli & Shop

Eleventy 3 site using Nunjucks, Tailwind CSS 4, and Alpine.js. Keep changes simple and use the existing structure before adding abstractions.

## Setup and build

- Use Node 24 or newer.
- Install dependencies with `npm install`.
- Run `npm run dev` for Eleventy, Tailwind, and JavaScript watchers at `http://localhost:8080`.
- Run `npm run build` for a production build in `_site/`. It bundles JS, compiles/minifies Tailwind, then runs Eleventy.
- Do not run a production build unless the user explicitly requests one.
- Run `npm run lint` before handing work off.
- Use Prettier as the preferred formatter. Run `npm run format` for source files.
- Development HTML is formatted with Prettier automatically; production HTML is minified.
- Set `SITE_URL` to the public origin when making a deployment build so canonical and social URLs are correct.
- Never edit `_site/` or `.cache/`; both are generated.

## Project layout

- Pages live in `src/pages/`.
- Shared layouts, partials, and macros live in `src/_includes/`.
- Site-wide YAML data lives in `src/_data/`.
- Eleventy extensions live in `config/`.
- Files in `src/static/` are copied to the site root.

## Tailwind and UI

- Prefer native inline Tailwind classes in Nunjucks templates.
- Tailwind scans `src/**/*.{njk,md,html,js}` from `src/assets/css/main.css`.
- Reuse the existing color tokens and utilities before adding CSS.
- Put genuinely shared styles in the existing files under `src/assets/css/`.
- Avoid dynamically assembled class names; Tailwind needs complete class strings at build time.
- Keep Alpine behavior small and local. Shared JavaScript belongs in `src/assets/js/main.js`.

## Images and assets

- Put site images in `src/assets/images/` and reference them as `/assets/images/<file>`.
- Put fonts in `src/assets/fonts/`; both image and font folders are copied through by Eleventy.
- HTML images are processed by the Eleventy image transform into AVIF/WebP/original variants at widths up to 1200px.
- Use meaningful alt text for informative images and `alt=""` for decorative images.
- Use `eleventy:ignore` only when an image must pass through untouched.
- The social card is `src/assets/images/og.png`; update `src/_data/metadata.yaml` if its path changes.
- Root assets such as the favicon and web manifest belong in `src/static/`.
- Delivery-provider SVGs live in `src/static/providers/`.

## Content

- Keep the Maxx Deli & Shop voice direct, friendly, and neighborhood-focused.
- Keep the confirmed address, phone, hours, and delivery providers consistent across the Home and About pages.
- Placeholder links should use `href="#"` with Alpine's `@click.prevent` until real URLs are supplied.
- Update metadata, manifest copy, and structured page content together when branding changes.

## Deployment

Netlify, Vercel, and Cloudflare Workers configs all publish `_site/`. Keep deployment-specific changes aligned across their config files when relevant.
