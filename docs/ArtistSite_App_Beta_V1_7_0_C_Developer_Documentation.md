# OMS Artist Site [Beta V1_7_0] - DEVELOPER DOCUMENTATION

**Current Date:** 2026-02-13  
**Current UNIX Epoch:** 1771027200  
**App Version:** Beta V1_7_0  
**App License:** GPL-3.0  
**Document Line Count:** ~260  
**Document Purpose:** Technical implementation reference for developers

---

## TABLE OF CONTENTS

1. [Architecture Overview](#1-architecture-overview)
2. [Page Structure](#2-page-structure)
3. [SPA Routing](#3-spa-routing)
4. [SEO Metadata](#4-seo-metadata)
5. [WebGPU Shaders](#5-webgpu-shaders)
6. [Mobile Responsive](#6-mobile-responsive)
7. [Image Map](#7-image-map)
8. [Known Dead CSS](#8-known-dead-css)

---

## 1. ARCHITECTURE OVERVIEW

### Single-File Philosophy

OMS Artist Site is a single HTML file containing all HTML, CSS, and JavaScript. This enables:
- Zero installation (open in browser)
- Offline capability
- Portability (copy file anywhere)
- No build process required

**URL:** https://onemanshyo.com/  
**Architecture:** Single HTML file, SPA with hash routing  
**Platform:** Chrome desktop (WebGPU required), mobile responsive  

---

## 2. PAGE STRUCTURE

### HOME (#home)
- Custom banner (340px) with draggable overlay panels (desktop only)
- YouTube player panel with auto-rotation (YouTube Data API v3, desktop only)
- Bio section with greeting, text, and signoff
- Highlights section (link cards)
- Marquee bar (fade on desktop, horizontal scroll on mobile)

### NEATO (#neato)
- Project-hero banner (340px) with "Neato" title overlay
- 5 image cards in app-grid (2-column desktop, 1-column mobile): Bass Cutter, Brick Fitnesss, Yobots, Yobotics, Yomatics
- Each card links to sub-page

### NEATO Sub-Pages
- #neato-bass-cutter, #neato-brick-fitness, #neato-yobots, #neato-yobotics, #neato-yomatics
- Project-hero banner with title overlay
- project-section panels with cyan headers
- project-text (24px prose), project-spec (21px specs)
- project-gallery (16:9 images, 2-column grid)
- Back link to home

### APPS (#apps)
- Project-hero banner (340px) with "Apps" title overlay
- 2 image cards in app-grid: ONEMANSHYO, StudiYo Partner
- Each card links to sub-page

### APPS Sub-Pages
- #apps-onemanshyo, #apps-studiyo-partner
- Same structure as NEATO sub-pages

### SHOP (#shop)
- Project-hero banner (340px) with "Yodega" title + "Yo + Bodega" subtitle
- 2 image cards in app-grid: Shop (→ Shopify), Support (→ YouTube)
- Hat product images as card backgrounds

### ABOUT (#about)
- Project-hero banner (340px) with "About This Site" title + subtitle
- 2×2 app-grid of about-section panels (200px fixed height):
  - APPLICATION: App name, version, license, author, built with
  - TECHNOLOGY: Architecture, platform, APIs (tag badges), shaders
  - MUSIC TOOLS ECOSYSTEM: OMS, StudiYo Partner, Artist Site
  - LINKS: GitHub, YouTube, Email List

---

## 3. SPA ROUTING

Hash-based routing via `window.addEventListener('hashchange', ...)`.
All sections use `.page-section` class, toggled via `.active`.

### Routes

| Hash | Page |
|------|------|
| #home | HOME |
| #neato | NEATO root |
| #neato-bass-cutter | Bass Cutter sub-page |
| #neato-brick-fitness | Brick Fitnesss sub-page |
| #neato-yobots | Yobots sub-page |
| #neato-yobotics | Yobotics sub-page |
| #neato-yomatics | Yomatics sub-page |
| #apps | APPS root |
| #apps-onemanshyo | ONEMANSHYO sub-page |
| #apps-studiyo-partner | StudiYo Partner sub-page |
| #shop | SHOP |
| #about | ABOUT |

### Route Handler Behaviors
- Toggles `.active` class on matching `.page-section`
- Scrolls to top on route change
- Closes mobile nav menu on navigation (`navLinks.classList.remove('mobile-open')`)

---

## 4. SEO METADATA

```
Title: OneManShYo | Music, Software and Shenanigans for the Modern DIY DJ & Producer
Description: Music, software and shenanigans for the modern DIY DJ & Producer. Open source tools, WebGPU visuals, and electronic music by Wes Smith.
Canonical: https://onemanshyo.com/
OG Image: https://onemanshyo.com/img/home/home_banner.png
OG Type: website
OG Site Name: OneManShYo
Twitter Card: summary_large_image
Author: Wes Smith
```

---

## 5. WEBGPU SHADERS

### Banner Pixelation
- Renders banner image through WebGPU pixelation effect
- Desktop only — not available on mobile browsers
- Shader version tagged in code comments

### Particle Cursor Trail
- WebGPU compute + render pipeline
- 1,024 particles (doubled from 512 in V1_5)
- Particles spawn at mouse position with random velocity
- Compute shader handles physics, render shader draws as points
- Canvas overlaid at z-index 9999, pointer-events: none
- Desktop only — not available on mobile browsers

---

## 6. MOBILE RESPONSIVE

### Breakpoint
`@media (max-width: 768px)` — all mobile overrides

### Navigation
- Hamburger button (three-line icon) replaces horizontal nav links
- `.nav-hamburger` hidden by default, `display: flex` at ≤768px
- Tap toggles `.mobile-open` class on `.nav-links`
- Menu: absolute positioned, full-width dropdown below nav bar
- Background: `rgba(12, 12, 12, 0.98)` with backdrop blur
- Parent items: 13px, 600 weight, uppercase, `#e0e0e0`
- Sub-items: 12px, 400 weight, indented to 44px, `#aaa`
- Menu closes on route change via `handleRoute()`

### Banner Panels
Hidden on mobile (`display: none`). WebGPU not supported on mobile browsers.

### Image Cards
- Text flows full width (removes `margin-right: 50%`)
- Gradient replaced with uniform dark overlay: `rgba(18,18,18,0.75)`
- Description text brightened to `#e0e0e0` with text shadow
- Card button divs have `z-index: 2` to render above overlay

### Marquee
- Desktop: fade/dissolve between items (opacity transition)
- Mobile: horizontal scroll animation (`marquee-scroll` keyframe, 8s duration)

### Grid
Falls back to single column at 600px (existing `@media (max-width: 600px)` rule).

### CSS Cascade Note
Mobile overrides are placed at the end of the stylesheet to win cascade conflicts against duplicate CSS declarations earlier in the file. This is a workaround — duplicate declarations should be cleaned in a future pass.

---

## 7. IMAGE MAP

### Card Background Images

| Card | Image Path |
|------|-----------|
| Bass Cutter | img/bass-cutter/Basscutter_Numark_Banner.jpg |
| Brick Fitnesss | img/brick-fitness/BrickFitness_Rezzonate_Scene1.png |
| Yobots | img/yobots/YoBotz_BurningMan_LEDDay1.jpg |
| Yobotics | img/yobotics/Yobotics_Banner.png |
| Yomatics | img/yomatics/Yomatics_Donkey.png |
| ONEMANSHYO | img/onemanshyo/OMS_hero_banner.png |
| StudiYo Partner | img/studiyo-partner/StudiYoPartner_Icon_Borderless.png |
| Shop | img/shop/shop_yocap_green.png |
| Support | img/shop/shop_yocap_rooster.png |

### Hero Banners
All root pages use `img/home/home_banner.png` for hero banners.
Sub-pages use their own images from respective img/ subdirectories.

---

## 8. KNOWN DEAD CSS

The following CSS classes are defined but no longer referenced in HTML. Harmless but should be cleaned in a future pass:

- `.shop-panel-img` — replaced by app-card-img
- `.shop-text` — replaced by app-desc
- `.shop-signoff` — removed
- `.shop-link` — replaced by inline button
- `.about-content` — replaced by page-content
- Various duplicate CSS blocks in media query section
- `.neato-card`, `.neato-grid` — replaced by app-card, app-grid

---

**END OF DOCUMENT**
