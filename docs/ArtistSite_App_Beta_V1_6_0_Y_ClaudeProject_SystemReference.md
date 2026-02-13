# OMS Artist Site [Beta V1_6_0] - SYSTEM REFERENCE

**Current Date:** 2026-02-09  
**Current UNIX Epoch:** 1770631200  
**App Version:** Beta V1_6_0  
**App License:** GPL-3.0  
**Document Line Count:** ~2,700  
**Document Purpose:** Design system, architecture, and development process reference

---

## TABLE OF CONTENTS

1. [Design System Components](#1-design-system-components)
2. [Color Palette](#2-color-palette)
3. [Typography](#3-typography)
4. [Component Specifications](#4-component-specifications)
5. [Image Card Gradient](#5-image-card-gradient)
6. [Folder Structure](#6-folder-structure)
7. [File Naming Convention](#7-file-naming-convention)
8. [Release Process](#8-release-process)
9. [Development Iteration Process](#9-development-iteration-process)
10. [Deliverables Per Release](#10-deliverables-per-release)
11. [Version String Locations](#11-version-string-locations)
12. [Design System Rules](#12-design-system-rules)

---

## 1. DESIGN SYSTEM COMPONENTS

| Component | Classes | Height | Radius | Used On |
|-----------|---------|--------|--------|---------|
| Image card | `app-card app-card-img` | 200px fixed | 8px | NEATO, APPS, SHOP roots |
| Panel card | `about-section` + `about-section-title` | 200px (About), auto (sub-pages) | 8px | About, sub-pages |
| Plain card | `app-card` + `app-name` + `app-desc` | auto | 8px | Fallback (no image) |
| Grid | `app-grid` | N/A | N/A | All root pages, About |
| Footer column | `footer-col` + `footer-col-header` + `footer-card` | auto | 8px | Footer |
| Hero banner | `project-hero` + `project-title` | 340px | none | All pages except HOME |
| Gallery | `project-gallery` | 16:9 per image | none | Sub-pages |

---

## 2. COLOR PALETTE

### CSS Custom Properties

| Token | Value | Usage |
|-------|-------|-------|
| `--cyan` | #00d4ff | Panel headers, active nav, links |
| `--magenta` | #ff006e | App tags |
| `--orange` | #ffa500 | Footer headers, nav app label |
| `--green` | #00ff88 | Concept tags |
| `--text-primary` | #e0e0e0 | Body text |
| `--text-secondary` | #888 | Secondary text, labels |
| `--text-dim` | #555 | Tertiary text |
| `--bg-dark` | #0c0c0c | Page background |
| `--bg-mid` | #1a1a1a | Mid background |
| `--border` | #333 | Border color |

### Surface Colors

| Token | Value | Usage |
|-------|-------|-------|
| `--surface-bg` | rgba(255,255,255,0.05) | Card/panel background |
| `--surface-hover` | rgba(255,255,255,0.08) | Hover state (currently removed from cards) |
| `--surface-active` | rgba(255,255,255,0.12) | Active state |

---

## 3. TYPOGRAPHY

| Context | Size | Weight | Color |
|---------|------|--------|-------|
| Panel headers (`app-name`, `about-section-title`) | 11px | 600 | #00d4ff |
| Card descriptions (`app-desc`) | 18px | 400 | #aaa |
| Sub-page prose (`project-text`) | 24px | 400 | #888 |
| Sub-page specs (`project-spec`) | 21px | 400 | #888 |
| About row labels | 13px | 600 | #888 |
| About row values | 13px | 400 | #e0e0e0 |
| Footer links (`footer-card`) | 11px | 400 | #888 |
| Nav links | 11px | 600 | #888 |
| Bio greeting | 34px | 700 | #e0e0e0 |
| Bio text | 20px | 400 | #888 |
| Section headers | 11px | 600 | #555 |

### Font Stack
```css
font-family: 'SF Pro Display', -apple-system, BlinkMacSystemFont, sans-serif;
```

---

## 4. COMPONENT SPECIFICATIONS

### Panel Headers (Cyan)
```css
font-size: 11px;
font-weight: 600;
text-transform: uppercase;
letter-spacing: 0.5px;
color: #00d4ff;
padding-bottom: 6px;
margin-bottom: 6px;
border-bottom: 1px solid rgba(255,255,255,0.05);
```

### App Grid
```css
display: grid;
grid-template-columns: 1fr 1fr;
gap: 12px;
margin-bottom: 16px;
```

### App Card
```css
background: rgba(255,255,255,0.05);
padding: 10px 10px;
border-radius: 8px;
text-decoration: none;
color: #e0e0e0;
display: flex;
flex-direction: column;
gap: 2px;
text-align: left;
```

### App Card Image
```css
position: relative;
height: 200px;
background-size: cover;
background-position: center;
overflow: hidden;
border-radius: 8px;
```

### Project Hero
```css
margin-top: 44px;
width: 100%;
height: 340px;
overflow: hidden;
position: relative;
```

### Gallery Images
```css
aspect-ratio: 16/9;
object-fit: cover;
```

---

## 5. IMAGE CARD GRADIENT

```css
/* Overlay: image right, text left */
background: linear-gradient(to left, transparent 20%, rgba(18,18,18,0.85) 50%, rgba(18,18,18,1) 65%);
```

Text constrained to left half via:
```css
.app-card-img .app-name,
.app-card-img .app-desc {
    position: relative;
    z-index: 2;
    margin-right: 50%;
}
```

---

## 6. FOLDER STRUCTURE

### Why Two Copies of HTML

Unlike OMS Main App (self-contained HTML, no external refs), the Artist Site HTML references external image assets in `img/`. This means deployment requires the HTML to sit alongside its `img/` folder. The result is two copies of the HTML:

- **Deliverables/** — Archive of MDs + HTML. Record of what shipped. This is the deliverables package.
- **web/** — HTML + img/. This is what gets deployed to GitHub Pages.

### Project Root
```
.../ArtistSite/App/Builds/V1/
├── V1_1_0/
├── V1_2_0/
├── V1_3_0/
├── V1_4_0/
├── V1_5_0/
└── V1_6_0/                                        ← Current release
    ├── ArtistSite_App_Beta_V1_6_0_Deliverables/   ← Archive (MDs + HTML)
    │   ├── ArtistSite_App_Beta_V1_6_0.html
    │   ├── ArtistSite_App_Beta_V1_6_0_A_Deliverables.md
    │   ├── ArtistSite_App_Beta_V1_6_0_B_Complete_Changelog.md
    │   ├── ArtistSite_App_Beta_V1_6_0_C_Developer_Documentation.md
    │   ├── ArtistSite_App_Beta_V1_6_0_D_Release_Notes.md
    │   ├── ArtistSite_App_Beta_V1_6_0_E_UserGuide.md
    │   ├── ArtistSite_App_Beta_V1_6_0_Y_ClaudeProject_SystemReference.md
    │   └── ArtistSite_App_Beta_V1_6_0_Z_ClaudeProject_Instructions.md
    └── web/                                        ← Deployment (HTML + img/)
        ├── ArtistSite_App_Beta_V1_6_0.html
        └── img/
            ├── home/
            ├── bass-cutter/
            ├── brick-fitness/
            ├── yobots/
            ├── yobotics/
            ├── yomatics/
            ├── onemanshyo/
            ├── studiyo-partner/
            └── shop/
```

### Version Folder Template
```
V[X_X_0]/
├── ArtistSite_App_Beta_V[X_X_0]_Deliverables/   ← Archive
│   ├── ArtistSite_App_Beta_V[X_X_0].html
│   └── ArtistSite_App_Beta_V[X_X_0]_[A-Z]_*.md
└── web/                                           ← Deployment
    ├── ArtistSite_App_Beta_V[X_X_0].html
    └── img/
```

---

## 7. FILE NAMING CONVENTION

### Application
```
ArtistSite_App_Beta_V[MAJOR]_[MINOR]_[ITERATION].html
```

Examples:
- `ArtistSite_App_Beta_V1_6_0.html` — release build
- `ArtistSite_App_Beta_V1_6_01.html` — first dev iteration
- `ArtistSite_App_Beta_V1_6_38.html` — 38th dev iteration

### Documents
```
ArtistSite_App_Beta_V[MAJOR]_[MINOR]_[RELEASE]_[LETTER]_[Name].md
```

Examples:
- `ArtistSite_App_Beta_V1_6_0_A_Deliverables.md`
- `ArtistSite_App_Beta_V1_6_0_B_Complete_Changelog.md`
- `ArtistSite_App_Beta_V1_6_0_Y_SystemReference.md`

### Document Header Template
```markdown
# OMS Artist Site [Beta V[XX_XX_X]] - [DOCUMENT TYPE]

**Current Date:** YYYY-MM-DD
**Current UNIX Epoch:** [seconds]
**App Version:** Beta V[XX_XX_X]
**App License:** GPL-3.0
**Document Line Count:** ~X,XXX
**Document Purpose:** [one-line description]
```

---

## 8. RELEASE PROCESS

### Create New Version

```bash
# 1. Create folder structure
mkdir -p '.../Builds/V1/V[X_X_0]/ArtistSite_App_Beta_V[X_X_0]_Deliverables'
mkdir -p '.../Builds/V1/V[X_X_0]/web/img'

# 2. Copy img/ from prior version
cp -r '.../Builds/V1/V[OLD]/web/img/'* '.../Builds/V1/V[X_X_0]/web/img/'

# 3. Copy release HTML into BOTH locations
cp ~/Downloads/ArtistSite_App_Beta_V[X_X_0].html '.../Builds/V1/V[X_X_0]/web/'
cp ~/Downloads/ArtistSite_App_Beta_V[X_X_0].html '.../Builds/V1/V[X_X_0]/ArtistSite_App_Beta_V[X_X_0]_Deliverables/'

# 4. Move deliverable MDs into Deliverables folder
mv ~/Downloads/ArtistSite_App_Beta_V[X_X_0]_*.md '.../Builds/V1/V[X_X_0]/ArtistSite_App_Beta_V[X_X_0]_Deliverables/'

# 5. Verify
find '.../Builds/V1/V[X_X_0]' -maxdepth 3 -not -name '.DS_Store' -not -path '*/img/*' | sort
```

### Key Difference from OMS Main App

OMS Main App is fully self-contained (no external refs), so the HTML only needs to live in the Deliverables folder. Artist Site HTML references `img/` assets, so the HTML must also live in `web/` alongside `img/` for deployment. Always copy the HTML to both locations on release.

---

## 9. DEVELOPMENT ITERATION PROCESS

### Each Change = New Iteration

```bash
# Claude delivers iteration HTML, Wes moves it into web/:
mv ~/Downloads/ArtistSite_App_Beta_V1_7_0X.html '.../Builds/V1/V1_7_0/web/'

# Test via local server:
cd '.../Builds/V1/V1_7_0/web'
python3 -m http.server 8001
# Browse: localhost:8001/ArtistSite_App_Beta_V1_7_0X.html
```

### Version String Update Checklist
Every iteration must update ALL version string locations (see Section 11).

---

## 10. DELIVERABLES PER RELEASE

| Letter | File | Purpose |
|--------|------|---------|
| A | `_A_Deliverables.md` | Package contents manifest |
| B | `_B_Complete_Changelog.md` | Full development history |
| C | `_C_Developer_Documentation.md` | Technical implementation reference |
| D | `_D_Release_Notes.md` | User-facing changes |
| E | `_E_UserGuide.md` | Deployment and hosting guide |
| Y | `_Y_SystemReference.md` | Design system & architecture (this file) |
| Z | `_Z_ClaudeProject_Instructions.md` | Claude development instructions |

---

## 11. VERSION STRING LOCATIONS

These locations must be updated every iteration:

| Location | Example |
|----------|---------|
| `<title>` tag | (SEO title — does not contain version) |
| Nav brand `.nav-version` | `[V1_6_0]` |
| About page row value | `V1_6_0` |
| Banner shader comment | `/* Banner WebGPU Pixelation Shader - V1_6_0 */` |
| Particle shader comment | `/* Particle Cursor Trail - WebGPU Compute + Render - V1_6_0 */` |
| `<!-- App Version: -->` comment in head | `<!-- App Version: V1_6_0 -->` |

---

## 12. DESIGN SYSTEM RULES

### No One-Off Classes
All similar objects must use established component classes. Do not create new classes for objects that already have a design system component.

**Bad:** Creating `.shop-panel-img` when `app-card-img` already exists.  
**Good:** Reusing `app-card app-card-img` + `app-name` + `app-desc`.

### Consistent Border Radius
All cards, panels, and footer columns: `border-radius: 8px`.

### No Hover Effects on Panels
Cards and panels do not have background transitions or hover state changes.

### Hero Banner Consistency
All root pages (except HOME) use `project-hero` at 340px. This matches the HOME banner height and eliminates page jumps during navigation.

### Panel Header Pattern
All panels use the same cyan header:
- 11px, 600 weight, uppercase, 0.5px letter-spacing
- Color: #00d4ff
- Bottom border: 1px solid rgba(255,255,255,0.05)
- Padding-bottom: 6px, margin-bottom: 6px

### Grid Layout
Two-column grid (`1fr 1fr`) with 12px gap. Falls back to single column at 600px viewport.

### Gallery Images
Always 16:9 aspect ratio with `object-fit: cover`.

---

**END OF DOCUMENT**
