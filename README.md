# Summit Arena — Static Archive

[Summit Arena FBLA - Accompanying Presentation][Web Design 24-25_AveryBehring.pptx]

A static, browsable snapshot of the Summit Arena website — an event venue project (Heath, OH) originally built on WordPress with the Divi theme, The Events Calendar, and Event Tickets.

This isn't a live business site. It's a reconstructed archive kept for portfolio/showcase purposes after the original hosted WordPress site was taken down. It was rebuilt by:

1. Restoring an UpdraftPlus backup (database, theme, plugins, uploads) into a local WordPress + MariaDB environment (Docker).
2. Letting WordPress + Divi render every page exactly as they looked live.
3. Crawling the rendered site into flat, dependency-free static HTML/CSS/JS/images with `wget --mirror`.

## What works vs. what doesn't

- **Home, Visiting Guide, Event Planning, About, Events & Tickets** pages are faithful static reproductions of the original design and copy.
- **Individual event pages** (`/event/...`) are included as static snapshots. Their dates were shifted forward so they read as "upcoming" — they are sample/demo event entries from the original site, not real scheduled events.
- **Calendar page** shows the page layout, but its interactive month-grid widget depended on a live WordPress REST API and will not populate on a static host — it's included as a visual mockup only.
- **Tickets Checkout / Order Completed** pages are static mockups of the checkout flow UI. No purchase functionality works — there's no backend.
- Some leftover content from the original build is preserved as-is (e.g. an internal "Page Will Include" outline note on the About page, generic placeholder event names, and placeholder testimonials) — this is an honest snapshot of the site as it existed, not something added during the rebuild.

## Structure

Every page is plain HTML with relative asset paths under `wp-content/`, `wp-includes/`, and vendor CDN mirrors — no server, database, or WordPress runtime required.
