# OMS Artist Site [Beta V1_6_0] - RELEASE NOTES

**Current Date:** 2026-02-09  
**Current UNIX Epoch:** 1770631200  
**App Version:** Beta V1_6_0  
**App License:** GPL-3.0  
**Document Line Count:** ~2,700  
**Document Purpose:** User-facing release summary for V1_6_0

---

## SUMMARY

V1_6_0 introduces a unified panel and card system across all pages, image card backgrounds with gradient fade treatment, full SEO metadata, and design standardization including 8px border-radius on all components and removal of hover effects.

---

## WHAT'S NEW

### Panel System
All content panels now share consistent styling — `rgba(255,255,255,0.05)` background, 10px padding, cyan (#00d4ff) uppercase headers with subtle bottom borders, and 8px border-radius. This applies to About page panels, sub-page project sections, and footer columns.

### Image Cards
NEATO, APPS, and SHOP root pages now feature image card backgrounds pulled from each project's hero image. Cards use a gradient fade from right to left, with text on the left side and the image visible on the right. All image cards are fixed at 200px height.

### Hero Standardization
All root pages (APPS, NEATO, SHOP, ABOUT) now use the same project-hero pattern with title overlaid on the banner image. Height standardized to 340px across all pages to eliminate the 60px jump when navigating from HOME.

### About Page Grid
About page converted from single-column stacked panels to a 2×2 grid layout (APPLICATION + TECHNOLOGY on top, MUSIC TOOLS ECOSYSTEM + LINKS on bottom) using the standard app-grid component.

### Shop Page
Single shop description panel replaced with two-column image card layout — Shop (green hat) and Donate (rooster hat) — using the same app-card-img component as NEATO and APPS.

### SEO
Full metadata added to `<head>`: title tag, meta description, canonical URL (onemanshyo.com), Open Graph tags for social sharing, and Twitter Card tags. Banner image used as OG image.

### Visual Polish
- 8px border-radius on all cards, panels, and footer columns
- Hover effects removed from all panels (was causing unwanted movement)
- Gallery images standardized to 16:9 aspect ratio
- Particle cursor trail doubled (512 → 1024 particles)
- App name updated to "artist site app" in nav brand

---

## STATISTICS

| Metric | Value |
|--------|-------|
| Development Period | February 7-9, 2026 |
| Iterations | 31 (V1_5_08 through V1_5_38) |
| Previous Version | V1_5_0 |

---

## FEEDBACK

- Social: @itswessmithyo
- YouTube: @itswessmithyo
- Website: https://onemanshyo.com

---

**END OF DOCUMENT**
