# Gym Mega Forme — static mirror notes

**Source:** https://www.gymmegaforme.com (Shopify storefront, French / Canada)  
**Captured:** 2026-09-24 (America/Toronto)  
**Tooling:** `wget` (page-requisites + convert-links), then post-processed for GitHub Pages / local `index.html`.

## What was captured

- Homepage (`index.html`)
- Collections: `collections/abonnements.html`, `collections/autres.html`
- Products (12): under `products/*.html` (abonnements, laissez-passer, frais, etc.)
- Pages: À propos, FAQ, Nous joindre, Photos, Termes et conditions, and a few other public Shopify pages
- Blog: `blogs/news.html` + one post
- Theme assets: CSS (`cdn/shop/t/3/assets/style.scss.css`), JS, fonts, logo, hero/lower images
- Product/collection images under `cdn/shop/files/` and `cdn/shop/products/`
- Page images under `s/files/...`
- Vendor JS needed for layout: jQuery, WebFont, html5shiv (under `ajax/libs/`)

Asset filenames had Shopify `?v=` cache-busters stripped so files serve correctly on GitHub Pages and `file://`.

Internal storefront links were rewritten to relative `.html` paths where local copies exist. Absolute links to **cart / account / checkout** were left pointing at the live site (they cannot work offline).

## What will NOT work offline

- **Cart, checkout, and payment** — require Shopify backend / Shop Pay; not mirrored by design
- **Customer account login / register** — not mirrored
- **Search** — Shopify search endpoint disabled in the mirror
- **Add to cart / dynamic inventory / price AJAX** — Shopify Storefront APIs won’t run against this static copy
- Some Shopify cloud scripts (`shop.app` preloads, portable wallets, Shop Pay) may 404 or no-op offline; they are not required to read content
- Instagram feed widgets (Instafeed) need a live API token/network

## Suggested use

Open `index.html` locally, or publish this folder as a GitHub Pages site from the **repo root** (keep `index.html` at root). A zip of the folder is fine for sharing or uploading.

## Politeness

Crawl used modest rate limiting (`--wait` / `--limit-rate`) against the public storefront only.
