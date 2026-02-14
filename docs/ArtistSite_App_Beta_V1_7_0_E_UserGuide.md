# OMS Artist Site [Beta V1_7_0] - USER GUIDE

**Current Date:** 2026-02-13  
**Current UNIX Epoch:** 1771027200  
**App Version:** Beta V1_7_0  
**App License:** GPL-3.0  
**Document Line Count:** ~170  
**Document Purpose:** Deployment and hosting guide for OMS Artist Site

---

## TABLE OF CONTENTS

1. [Prerequisites](#1-prerequisites)
2. [Repository Structure](#2-repository-structure)
3. [GitHub Pages Setup](#3-github-pages-setup)
4. [Custom Domain](#4-custom-domain)
5. [Local Development](#5-local-development)
6. [Deploying Updates](#6-deploying-updates)
7. [Mobile Testing](#7-mobile-testing)
8. [SEO Verification](#8-seo-verification)

---

## 1. PREREQUISITES

- GitHub account
- Git installed locally
- Custom domain (optional)
- Chrome browser (WebGPU required for desktop shader effects)

---

## 2. REPOSITORY STRUCTURE

```
[repo-root]/
├── index.html          ← Main application
├── CNAME               ← Custom domain (auto-created by GitHub)
├── img/                ← Image assets
│   ├── home/
│   ├── bass-cutter/
│   ├── brick-fitness/
│   ├── yobots/
│   ├── yobotics/
│   ├── yomatics/
│   ├── onemanshyo/
│   ├── studiyo-partner/
│   ├── logos/
│   └── shop/
└── docs/               ← Documentation
    ├── *_A_Deliverables.md
    ├── *_B_Complete_Changelog.md
    ├── *_C_Developer_Documentation.md
    ├── *_D_Release_Notes.md
    ├── *_E_UserGuide.md
    ├── *_Y_ClaudeProject_SystemReference.md
    └── *_Z_ClaudeProject_Instructions.md
```

---

## 3. GITHUB PAGES SETUP

1. Create a repo on GitHub (e.g., `onemanshyo`)
2. Clone it locally: `git clone git@github.com:[username]/[repo].git`
3. Copy `index.html`, `img/`, and `docs/` into the repo
4. Push:
```bash
git add -A
git commit -m "Initial deploy"
git push origin main
```
5. Go to repo → **Settings** → **Pages**
6. Source: **Deploy from a branch**
7. Branch: **main** / **root**
8. Save
9. Site live at `https://[username].github.io/[repo]/`

---

## 4. CUSTOM DOMAIN

### GitHub Side
1. Settings → Pages → Custom domain
2. Enter domain (e.g., `onemanshyo.com`)
3. GitHub auto-creates `CNAME` file in repo

### DNS Side
Add these records at your domain registrar:

**A Records (apex domain):**
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**CNAME Record (www):**
```
www → [username].github.io
```

### Verify
- Enable **Enforce HTTPS** in GitHub Pages settings
- DNS propagation: up to 24 hours
- Test: `https://onemanshyo.com/`

---

## 5. LOCAL DEVELOPMENT

### Start Dev Server
```bash
cd [path-to-iterations-folder]
python3 -m http.server 8001
```

### Browse
Desktop: `http://localhost:8001/[iteration-filename].html`

The server stays running. New iteration files dropped into the same folder are immediately accessible — just change the filename in the URL and refresh.

---

## 6. DEPLOYING UPDATES

From the `web/` folder inside your Deliverables:

```bash
cd [path-to-web-folder]
git add -A
git status                    # Review before committing
git commit -m "ArtistSite App Beta V[X_X_0] - [description]"
git push origin main
```

If push is rejected (remote has newer commits):
```bash
git pull origin main --rebase
git push origin main
```

GitHub Pages deploys automatically within a few minutes of push.

### View Commit History
- Web: https://github.com/ItsWesSmithYo/onemanshyo/commits/main
- Terminal: `git log --oneline`

---

## 7. MOBILE TESTING

### Same WiFi Network Required
Your Mac and phone must be on the same WiFi network.

### Get Mac IP
```bash
ipconfig getifaddr en0
```

### Browse on Phone
```
http://[MAC-IP]:8001/[iteration-filename].html
```

Type the full URL including `http://` — without it, mobile browsers treat it as a search query.

---

## 8. SEO VERIFICATION

### Test OG Tags
- https://developers.facebook.com/tools/debug/ (Facebook/Meta)
- https://cards-dev.twitter.com/validator (Twitter)
- Paste `https://onemanshyo.com/` to preview social share cards

### Verify
- Title shows in browser tab
- Meta description appears in Google search results (may take days to index)
- OG image (1200×630 recommended) displays on social shares
- Canonical URL resolves correctly

---

**END OF DOCUMENT**
