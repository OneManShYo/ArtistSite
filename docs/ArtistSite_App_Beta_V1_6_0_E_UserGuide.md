# OMS Artist Site [Beta V1_6_0] - USER GUIDE

**Current Date:** 2026-02-09  
**Current UNIX Epoch:** 1770631200  
**App Version:** Beta V1_6_0  
**App License:** GPL-3.0  
**Document Line Count:** ~2,700  
**Document Purpose:** Deployment and hosting guide for OMS Artist Site

---

## TABLE OF CONTENTS

1. [Prerequisites](#1-prerequisites)
2. [Repository Setup](#2-repository-setup)
3. [File Structure](#3-file-structure)
4. [GitHub Pages](#4-github-pages)
5. [Custom Domain](#5-custom-domain)
6. [Local Development](#6-local-development)
7. [Updating Content](#7-updating-content)
8. [SEO Verification](#8-seo-verification)

---

## 1. PREREQUISITES

- GitHub account
- Custom domain (optional)
- Chrome browser (WebGPU required for shader effects)

---

## 2. REPOSITORY SETUP

```bash
# Create repo on GitHub: onemanshyo.com (or preferred name)
git clone https://github.com/[username]/[repo-name].git
cd [repo-name]

# Copy release HTML and rename to index.html
cp OMS_ArtistSite_Beta_V1_6_0.html index.html

# Copy image assets
cp -r img/ img/

# Push
git add .
git commit -m "Initial deploy V1_6_0"
git push origin main
```

---

## 3. FILE STRUCTURE

```
[repo-root]/
├── index.html          ← Renamed from OMS_ArtistSite_Beta_V1_6_0.html
├── CNAME               ← Custom domain (optional)
└── img/
    ├── home/
    │   └── home_banner.png
    ├── bass-cutter/
    ├── brick-fitness/
    ├── yobots/
    ├── yobotics/
    ├── yomatics/
    ├── onemanshyo/
    ├── studiyo-partner/
    └── shop/
        ├── shop_yocap_green.png
        └── shop_yocap_rooster.png
```

---

## 4. GITHUB PAGES

1. Go to repo → **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / **root**
4. Save
5. Site live at `https://[username].github.io/[repo-name]/`

---

## 5. CUSTOM DOMAIN

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

## 6. LOCAL DEVELOPMENT

```bash
# Start local server from web/ folder
cd /path/to/ArtistSite_V1_6/web
python3 -m http.server 8001

# Browse to:
# localhost:8001/OMS_ArtistSite_Beta_V1_6_0.html
```

---

## 7. UPDATING CONTENT

### New Version Deploy
```bash
# Copy new HTML, rename to index.html
cp OMS_ArtistSite_Beta_V[NEW].html index.html

# Add any new images
cp -r new-images/ img/

# Push
git add .
git commit -m "Deploy V[NEW]"
git push origin main
```

### Adding a New Project
1. Add project images to `img/[project-name]/`
2. Add HTML section in the app (new page-section + route)
3. Add image card on parent root page
4. Update SPA routing in JavaScript
5. Deploy

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
