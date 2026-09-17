# Summit Arena — Static Archive

[Summit Arena FBLA - Accompanying Presentation](Web%20Design%2024-25_AveryBehring.pptx)

A static, browsable snapshot of the Summit Arena website — an event venue project (Heath, OH) originally built on WordPress with the Divi theme, The Events Calendar, and Event Tickets.

This isn't a live business site. It's a reconstructed archive kept for portfolio/showcase purposes after the original hosted WordPress site was taken down. It was rebuilt by:

1. Restoring an UpdraftPlus backup (database, theme, plugins, uploads) into a local WordPress + MariaDB environment (Docker).
2. Letting WordPress + Divi render every page exactly as they looked live.
3. Crawling the rendered site into flat, dependency-free static HTML/CSS/JS/images with `wget --mirror`.

## What works vs. what doesn't

- **Home, Visiting Guide, Event Planning, About, Events & Tickets** pages are faithful static reproductions of the original design and copy.
- **Individual event pages** (`/event/...`) are included as static snapshots. Their dates were shifted forward so they read as "upcoming" — they are sample/demo event entries from the original site, not real scheduled events.
- **Calendar page** renders the month grid and populates it from `assets/events-feed.json`, a static export of the six demo events. Navigating to the event months shows them with times, links and tooltips. The original widget fetched the same data from a live WordPress REST endpoint.
- **Visiting Guide map** is a styled placeholder. The original used a Divi Google Maps module, which needs a live Maps API key.
- **Tickets Checkout / Order Completed** pages are static mockups of the checkout flow UI. No purchase functionality works — there's no backend.
- Some leftover content from the original build is preserved as-is (e.g. an internal "Page Will Include" outline note on the About page, generic placeholder event names, and placeholder testimonials) — this is an honest snapshot of the site as it existed, not something added during the rebuild.

## Structure

Every page is plain HTML with relative asset paths under `wp-content/`, `wp-includes/`, and vendor CDN mirrors — no server, database, or WordPress runtime required.

## Archive repairs

The crawl captured Divi's inline "critical" CSS but not the deferred stylesheets
it pairs with, nor the Theme Builder's dynamic CSS — both were only ever served
from the WordPress origin. A number of pages also still pointed at that origin
for images. `assets/archive-fixes.css` restores the missing declarations
(blurb-icon visibility, header nav colours, pricing-table and contact-form
layout) and absolute `localhost` URLs were rewritten to relative paths.
