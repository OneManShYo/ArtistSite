# OMS Artist Site [Beta V1_7_0] - COMPLETE CHANGELOG

**Current Date:** 2026-02-13  
**Current UNIX Epoch:** 1771027200  
**App Version:** Beta V1_7_0  
**App License:** GPL-3.0  
**Document Line Count:** ~110  
**Document Purpose:** Complete development history for V1_7_0 release

---

## V1_7_0 — Mobile Responsive, Nav, Card Text, Dev Workflow

### Added
- **Mobile Hamburger Nav** — Three-line hamburger button at ≤768px, replaces horizontal nav. Tap toggles slide-down menu with stacked links. NEATO/APPS sub-items indented under parent headers. Menu closes on navigation.
- **Mobile Card Text** — Full-width text over image on mobile (removed `margin-right: 50%` constraint). Dark overlay (`rgba(18,18,18,0.75)`) over image for readability. Description text brightened to `#e0e0e0` with text shadow.
- **Mobile Marquee Scroll** — Horizontal scroll animation on mobile replaces desktop dissolve/fade behavior. 8-second scroll cycle matches JS rotation interval.
- **Git Deployment Docs** — New Section 13 in System Reference documenting repo, push workflow, commit format.
- **Iterations Folder Pattern** — Dev workflow using `Iterations/` folder with shared `img/` copy alongside `Deliverables/`.

### Changed
- **Shop "Donate" Card** — Replaced Buy Me a Coffee link with YouTube channel link. Title changed from "Donate" to "Support". Description updated. Button text changed to "YouTube →".
- **Shop Card Buttons** — Added `position:relative;z-index:2` to "Visit the Yodega →" and "YouTube →" buttons so they render above the mobile dark overlay.
- **Mobile Nav Text** — Parent items (HOME, NEATO, etc.) at `#e0e0e0`, sub-items (Bass Cutter, etc.) at `#aaa` for clear hierarchy.
- **Banner Panels** — Hidden on mobile via `display: none` (WebGPU not available on mobile browsers).
- **Folder Structure** — Corrected from V1_6_0: `web/` lives inside Deliverables (not at version root). Single `index.html` in `web/` (no duplicate HTMLs). Named archive HTML sits in Deliverables root alongside MDs.
- **Target Platform** — Expanded from "Chrome on MacBook Pro 14" only to include mobile responsive support.

### Removed
- **Buy Me a Coffee Integration** — Replaced with YouTube channel link.

### Dead CSS (Still Present, Harmless)
- `.shop-panel-img` — No longer used (shop uses app-card-img)
- `.shop-text`, `.shop-signoff`, `.shop-link` — No longer used
- `.about-content` — Replaced by page-content + app-grid
- Various duplicate CSS blocks from media query section (noted: causes cascade issues, mobile overrides placed at end of stylesheet to compensate)

---

## V1_6_0 — Panel System, Image Cards, SEO, Design Standardization

### Added
- **SEO Head** — Title tag, meta description, canonical URL (onemanshyo.com), Open Graph tags, Twitter Card tags
- **Image Cards** — Hero image backgrounds with gradient fade on NEATO root (5 cards), APPS root (2 cards), SHOP (2 cards)
- **Shop + Donate Panels** — Two-column layout on Shop page with hat product images
- **About Page Banner** — Standard project-hero with title overlay
- **About 2×2 Grid** — APPLICATION, TECHNOLOGY, ECOSYSTEM, LINKS panels in two rows of two
- **Gallery 16:9** — All gallery images standardized to `aspect-ratio: 16/9` with `object-fit: cover`
- **Border Radius** — 8px on all cards, panels, and footer columns
- **Particle Trail 2×** — `NUM_PARTICLES` doubled from 512 to 1024

### Changed
- **Root Page Heroes** — APPS, NEATO, SHOP, ABOUT converted from banner + page-title to project-hero + title overlay (matches sub-pages)
- **Banner Height** — project-hero standardized to 340px (matches HOME banner, eliminates page jump)
- **Sub-Page Panels** — project-section gets panel treatment (background, padding, cyan headers)
- **App Card Styling** — Redesigned with 11px uppercase cyan headers, 18px description text, left-aligned
- **Shop Page** — Single panel converted to two-column app-card grid (Shop + Donate)
- **About Page** — Single-column stacked panels converted to 2×2 app-grid layout with fixed 200px height
- **Nav Brand** — Recombined split links into single unit linking to #home, app name updated to "artist site app"
- **Card Height** — All image cards fixed at 200px (was min-height)
- **App Grid Margin** — 48px → 16px bottom margin (removed excess whitespace)

### Removed
- **Hover Effects** — Removed background transitions from all app-cards, neato-cards, highlights, link-cards
- **Project Tags** — Removed HARDWARE, SOFTWARE, CONCEPT, ART labels from all sub-pages (7 instances)
- **App Tags** — Removed from NEATO and APPS root cards

---

**Iterations:** V1_6_01 through V1_6_11 (11 iterations)  
**Previous Version:** V1_6_0 (31 iterations, V1_5_08 through V1_5_38)

---

**END OF DOCUMENT**
