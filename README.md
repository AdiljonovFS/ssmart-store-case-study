# SSMART — online store for appliances and electronics

**[ssmart.uz](https://ssmart.uz/)** · in production for a retailer in Qarshi, Uzbekistan

A storefront for a physical appliance and electronics shop: full catalogue, cart and checkout, instalment pricing on every product, and a live shopping channel.

![Product catalogue with instalment pricing](catalogue.png)

---

## The problem

The company sold from a physical shop in Qarshi. Customers outside the city had no way to browse stock or compare prices, and almost every purchase in this market is made on instalments — so a price tag alone doesn't answer the question people actually have, which is *what do I pay per month?*

## What the storefront does

**Catalogue** — categories for large appliances, small appliances, climate, cleaning, and electronics, plus a separate section for used iPhones. Search across the whole catalogue.

**Instalment pricing on every card** — alongside the price, each product shows its monthly payment at 0% over 12 months. The calculation runs on the product list, not just the detail page, so the comparison customers care about is visible while browsing.

**Cart, wishlist, and accounts** — saved favourites, cart state, and order history per user.

**Merchandising** — discount percentages, and badges for promotions, best sellers, warranty pricing, and new arrivals, all driven by product data rather than hardcoded.

**SSMART TV** — a live shopping channel built into the storefront.

**Ustalar** — a section for booking installation and repair technicians, which matters for appliances that need mounting.

---

## Architecture

The storefront is a React 19 SPA served by its own **Express** layer, which handles the API routes and serves the built client with compression. Keeping a small server in front of the SPA gave somewhere to put catalogue endpoints and response caching without standing up a separate service.

## Frontend work

- **Product listing at scale** — category pages, search, filtering, and image-heavy grids that stay fast on mobile connections
- **Instalment calculation** — monthly payment derived per product and rendered on every card
- **Cart and wishlist state** persisted across sessions
- **Live video integration** — the SSMART TV channel embedded in the storefront
- **Sales dashboards** with Recharts
- **Uzbek and Russian** via i18next with browser language detection, covering product data as well as UI strings
- **Responsive layout** — most traffic in this market is mobile

## Design decisions worth noting

Monthly payment is shown on the card, not hidden behind a click. It's one extra number per product and it removes the main reason a customer would leave to phone the shop.

Badges and discounts are data-driven, so the shop's staff can run a promotion without a deploy.

---

## Stack

`React 19` `Vite` `Tailwind CSS 4` `React Router 7` `Express` `i18next` `Recharts`

---

*Source code is private — this repository documents the work.*
