# OMS Artist Site [Beta V1_7_0] - SYSTEM REFERENCE

**Current Date:** 2026-02-13  
**Current UNIX Epoch:** 1771027200  
**App Version:** Beta V1_7_0  
**App License:** GPL-3.0  
**Document Line Count:** ~420  
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
13. [Git Deployment](#13-git-deployment)

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

### Desktop (default)
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

### Mobile (≤768px)
Text flows full width across image. Gradient replaced with uniform dark overlay:
```css
.app-card-img .app-name,
.app-card-img .app-desc {
    margin-right: 0 !important;
}
.app-card-img::before {
    background: rgba(18,18,18,0.75) !important;
}
```
Description text brightened to `#e0e0e0` with text shadow for readability.

---

## 6. FOLDER STRUCTURE

### Project Root
```
.../ArtistSite/App/Builds/V1/
├── V1_5_0/
├── V1_6_0/
│   ├── ArtistSite_App_Beta_V1_6_0_Deliverables/
│   │   ├── ArtistSite_App_Beta_V1_6_0.html       ← Named archive copy
│   │   ├── ArtistSite_App_Beta_V1_6_0_*_.md      ← Release docs
│   │   └── web/                                    ← Deployment package
│   │       ├── .git/                               ← Git repo (frozen at V1_6_0)
│   │       ├── index.html                          ← Deployed HTML
│   │       ├── img/                                ← Image assets
│   │       └── docs/                               ← Docs on GitHub
│   └── ArtistSite_App_Beta_V1_6_0_Iterations/     ← Dev work (V1_6_01–V1_6_11)
│       ├── ArtistSite_App_Beta_V1_6_01.html
│       ├── ArtistSite_App_Beta_V1_6_11.html
│       └── img/                                    ← Shared image assets for testing
└── V1_7_0/                                         ← Current release
    └── ArtistSite_App_Beta_V1_7_0_Deliverables/
        ├── ArtistSite_App_Beta_V1_7_0.html         ← Named archive copy
        ├── ArtistSite_App_Beta_V1_7_0_*_.md        ← Release docs
        └── web/                                     ← Deployment package
            ├── .git/                                ← Git repo (current)
            ├── index.html                           ← Deployed HTML
            ├── img/                                 ← Image assets
            └── docs/                                ← Docs on GitHub
```

### Key Principles

1. **`web/` lives inside Deliverables** — it is the deployment package. `index.html` + `img/` + `docs/` + `.git/`.
2. **One HTML in `web/`, named `index.html`** — GitHub Pages requires this name. No duplicate HTML files.
3. **Named archive HTML sits in Deliverables root** — `ArtistSite_App_Beta_V1_7_0.html` alongside the MDs. This is the record of what shipped.
4. **Iterations folder is for dev work only** — lives alongside Deliverables at the version root. Contains iteration HTMLs and a copy of `img/` for local testing.
5. **`img/` is a shared dependency** — copied once at version setup into both Deliverables/web/ and Iterations/. All iteration HTMLs reference the same `img/` with relative paths.
6. **Docs go to GitHub** — GPL-3.0 project, anyone who clones the repo gets the docs in `web/docs/`.

### Version Folder Template
```
V[X_X_0]/
├── ArtistSite_App_Beta_V[X_X_0]_Deliverables/
│   ├── ArtistSite_App_Beta_V[X_X_0].html          ← Named archive
│   ├── ArtistSite_App_Beta_V[X_X_0]_[A-Z]_*.md    ← Release docs
│   └── web/                                         ← Deployment
│       ├── .git/
│       ├── index.html
│       ├── img/
│       └── docs/
└── ArtistSite_App_Beta_V[X_X_0]_Iterations/        ← Dev work
    ├── ArtistSite_App_Beta_V[X_X_0]NN.html         ← Iteration files
    └── img/                                          ← Testing assets
```

---

## 7. FILE NAMING CONVENTION

### Application
```
ArtistSite_App_Beta_V[MAJOR]_[MINOR]_[ITERATION].html
```

Examples:
- `ArtistSite_App_Beta_V1_7_0.html` — release build (named archive)
- `ArtistSite_App_Beta_V1_7_01.html` — first dev iteration
- `ArtistSite_App_Beta_V1_7_11.html` — 11th dev iteration
- `index.html` — deployment copy in web/ (same content as release build)

### Documents
```
ArtistSite_App_Beta_V[MAJOR]_[MINOR]_[RELEASE]_[LETTER]_[Name].md
```

Examples:
- `ArtistSite_App_Beta_V1_7_0_A_Deliverables.md`
- `ArtistSite_App_Beta_V1_7_0_B_Complete_Changelog.md`
- `ArtistSite_App_Beta_V1_7_0_Y_ClaudeProject_SystemReference.md`

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
# Variables (update per release)
BASE='.../ArtistSite/App/Builds/V1'
VER='V1_8_0'
PREV='V1_7_0'

# 1. Create Deliverables structure
mkdir -p "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/web/docs"

# 2. Copy img/ from prior version
cp -r "$BASE/$PREV/ArtistSite_App_Beta_${PREV}_Deliverables/web/img" \
      "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/web/img"

# 3. Copy .git from prior version
cp -r "$BASE/$PREV/ArtistSite_App_Beta_${PREV}_Deliverables/web/.git" \
      "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/web/.git"

# 4. Place release HTML as index.html in web/
mv ~/Downloads/index.html "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/web/"

# 5. Place named archive HTML in Deliverables root
mv ~/Downloads/ArtistSite_App_Beta_${VER}.html \
   "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/"

# 6. Place docs in both Deliverables root and web/docs/
mv ~/Downloads/ArtistSite_App_Beta_${VER}_*.md \
   "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/"
cp "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/"*.md \
   "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/web/docs/"

# 7. Verify
ls "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/"
ls "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/web/"
```

### Create Iterations Folder (for next dev cycle)

```bash
# 1. Create Iterations folder
mkdir -p "$BASE/$VER/ArtistSite_App_Beta_${VER}_Iterations"

# 2. Copy img/ for local testing
cp -r "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/web/img" \
      "$BASE/$VER/ArtistSite_App_Beta_${VER}_Iterations/img"
```

---

## 9. DEVELOPMENT ITERATION PROCESS

### Setup (Once Per Version)

Create the Iterations folder with a copy of `img/` (see Section 8). The server runs from Iterations and stays running throughout development.

### Each Change = New Iteration File

```bash
# Claude delivers iteration HTML, Wes moves it into Iterations:
mv ~/Downloads/ArtistSite_App_Beta_V1_8_01.html \
   "$BASE/V1_8_0/ArtistSite_App_Beta_V1_8_0_Iterations/"
```

### Start Dev Server (Once)

```bash
cd "$BASE/V1_8_0/ArtistSite_App_Beta_V1_8_0_Iterations"
python3 -m http.server 8001
```

### Testing

Desktop: `http://localhost:8001/ArtistSite_App_Beta_V1_8_01.html`

Mobile (same WiFi):
```bash
ipconfig getifaddr en0   # Get Mac IP
```
Then on phone: `http://[IP]:8001/ArtistSite_App_Beta_V1_8_01.html`

New iterations: just change the number in the URL and refresh. No server restart needed.

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
| Y | `_Y_ClaudeProject_SystemReference.md` | Design system & architecture (this file) |
| Z | `_Z_ClaudeProject_Instructions.md` | Claude development instructions |

---

## 11. VERSION STRING LOCATIONS

These locations must be updated every iteration:

| Location | Example |
|----------|---------|
| `<title>` tag | (SEO title — does not contain version) |
| Nav brand `.nav-version` | `[V1_7_0]` |
| About page row value | `V1_7_0` |
| Banner shader comment | `/* Banner WebGPU Pixelation Shader - V1_7_0 */` |
| Particle shader comment | `/* Particle Cursor Trail - WebGPU Compute + Render - V1_7_0 */` |
| `<!-- App Version: -->` comment in head | `<!-- App Version: V1_7_0 -->` |

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

## 13. GIT DEPLOYMENT

### Repository

- **Repo:** github.com/ItsWesSmithYo/onemanshyo
- **Branch:** main
- **Deployed via:** GitHub Pages (main branch, root)
- **Live URL:** https://onemanshyo.com/

### Where `.git` Lives

The `.git` directory lives inside `Deliverables/web/`. This is the deployment package — `web/` IS the repo working directory. On each new version, `.git` is copied from the prior version's `web/` into the new version's `web/`.

### Deploy a New Version

```bash
cd "$BASE/$VER/ArtistSite_App_Beta_${VER}_Deliverables/web"
git add -A
git status          # Review changes before committing
git commit -m "ArtistSite App Beta $VER - [brief description]"
git push origin main
```

### Commit Message Format
```
ArtistSite App Beta V[X_X_0] - [Brief description of changes]
```

Examples:
- `ArtistSite App Beta V1_7_0 - Mobile responsive nav, banner panels, card text`
- `ArtistSite App Beta V1_8_0 - Translation system, personality modes`

### If Push Is Rejected
```bash
git pull origin main --rebase
git push origin main
```

### View History
- Web: https://github.com/ItsWesSmithYo/onemanshyo/commits/main
- Terminal: `git log --oneline`
- View old file: `git show [commit-hash]:index.html`

---

**END OF DOCUMENT**
