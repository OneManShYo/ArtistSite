# OMS Artist Site [Beta V1_6_0] - COMPLETE CHANGELOG

**Current Date:** 2026-02-09  
**Current UNIX Epoch:** 1770631200  
**App Version:** Beta V1_6_0  
**App License:** GPL-3.0  
**Document Line Count:** ~70  
**Document Purpose:** Complete development history for V1_6_0 release

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

### Design System Components (Standardized)

| Component | Classes | Used On |
|-----------|---------|---------|
| Image card | `app-card app-card-img` + `app-name` + `app-desc` | NEATO, APPS, SHOP |
| Panel card | `about-section` + `about-section-title` | About, sub-pages |
| Plain card | `app-card` + `app-name` + `app-desc` | Fallback (no image) |
| Footer column | `footer-col` + `footer-col-header` + `footer-card` | Footer |
| Hero banner | `project-hero` + `project-title` | All pages except HOME |

### Dead CSS (Still Present, Harmless)
- `.shop-panel-img` — No longer used (shop uses app-card-img)
- `.shop-text`, `.shop-signoff`, `.shop-link` — No longer used
- `.about-content` — Replaced by page-content + app-grid
- Various duplicate CSS blocks from media query section

---

**Iterations:** V1_5_08 through V1_5_38 (31 iterations consolidated)

---

**END OF DOCUMENT**
