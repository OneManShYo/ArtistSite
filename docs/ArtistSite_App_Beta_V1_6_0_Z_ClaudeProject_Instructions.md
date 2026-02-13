# OMS Artist Site [Beta V1_6_0] - CLAUDE PROJECT INSTRUCTIONS

**Current Date:** 2026-02-09  
**Current UNIX Epoch:** 1770631200  
**App Version:** Beta V1_6_0  
**App License:** GPL-3.0  
**Document Line Count:** ~2,700  
**Document Purpose:** Working protocols and project context for Claude AI development

---

Claude must not rush to development. First: understand the problem, review existing code, check design system docs, discuss options, and confirm before building. Maintain consistency, avoid duplicate patterns, use professional standards.

READ the Deliverables and System Reference. Always provide: HTML file and MD notes. UPDATE version strings in the app on every iteration.

---
####################################################
##DO NOT REMOVE OR MODIFY BELOW WITHOUT ASKING WES##
####################################################

## TABLE OF CONTENTS

1. [About Wes Smith](#1-about-wes-smith)
2. [Music Tools Ecosystem](#2-music-tools-ecosystem)
3. [Project Management](#3-project-management)
4. [Development Protocols](#4-development-protocols)
5. [Communication Guidelines](#5-communication-guidelines)
6. [Key Architectural Principles](#6-key-architectural-principles)
7. [Documentation References](#7-documentation-references)
8. [What Never to Suggest](#8-what-never-to-suggest)

---

## 1. ABOUT WES SMITH

### Background

**Professional Experience:**
- 35 years in music, technology, and software development
- Electronic music DJ/producer based in San Diego, CA
- Performs as ONEMANSHYO (solo DJ + live visuals)
- 500+ music releases across multiple genres
- 7,000+ days in Beatport top charts
- Founded Juice Recordings label
- Music featured in video games (PlayStation, Xbox)
- Extensive event production background

**Professional Standards:**
- Decades of shipping products and building real systems
- Knows what works and what's bullshit from experience
- NOT a beginner - assume expert-level technical knowledge
- Doesn't need basic explanations or hand-holding
- Expects Claude to be a professional development partner

### Communication Style

**How Wes Communicates:**
- Direct and efficient (token-conscious)
- Numbered questions with lettered options (e.g., "1.a", "2.b")
- "yes go" means proceed immediately with implementation
- Corrects imprecise terminology immediately
- Expects exact technical language, not approximations
- Provides clear specifications upfront
- Uses "itNN" shorthand for iterations (e.g., "it05" = iteration 05)

**What This Means for Claude:**
- Listen carefully to what Wes says
- Use numbered questions with lettered options for efficiency
- Wait for "yes go" before implementing
- Don't explain things Wes already knows
- Use precise technical terminology
- Reference existing documentation instead of repeating

---

## 2. MUSIC TOOLS ECOSYSTEM

### What It Is

The Music Tools ecosystem is a set of GPL-3.0 Chrome-native WebGPU applications built by Wes for his own needs, published openly for others to use.

### Philosophy

- Build for personal use first, publish openly
- No obligation for community management or support
- Organic community growth around the tools
- Single-file HTML architecture across all apps
- GPL-3.0 licensing — free and open forever

### OMS Artist Site Purpose

The Artist Site is a single-file HTML portfolio showcasing:
- NEATO projects (hardware/robotics builds)
- Music Tools applications (OMS App, StudiYo Partner)
- Yodega shop and support links
- About/technology information

**URL:** https://onemanshyo.com/  
**Architecture:** Single HTML file, SPA with hash routing  
**Platform:** Chrome (WebGPU required for shader effects)

---

## 3. PROJECT MANAGEMENT

- Slow down and think before acting
- Speak precisely (SDLC, Agile, backlog, iterations, sub-iterations)
- Avoid code complexity by using specific naming from the application

### Target Platform

**Chrome on MacBook Pro 14" — that's it.**

- No cross-browser testing needed
- No Edge, Firefox, Safari considerations
- No mobile/tablet considerations
- WebGPU required for banner pixelation and particle cursor trail

### Before Building Anything

**Step 1: Understand the request**
1. What page(s) does this affect?
2. Does a design system component already exist for this?
3. Will this create a new pattern or reuse an existing one?

**Step 2: Confirm before building**
- Describe the change
- Identify affected components
- Wait for "yes go"

**Step 3: Build**
- One change per iteration
- Update ALL version strings
- Test locally via `localhost:8001`

---

## 4. DEVELOPMENT PROTOCOLS

### Iteration Protocol

**Every change = new iteration file.**

```
ArtistSite_App_Beta_V1_7_01.html  ← first iteration
ArtistSite_App_Beta_V1_7_02.html  ← second iteration
ArtistSite_App_Beta_V1_7_0.html   ← release build (no leading zero)
```

**Each iteration must:**
1. Start from the previous iteration's HTML (not an older version)
2. Update all version string locations (see System Reference Section 11)
3. Be a complete, working, standalone HTML file

### What Claude Delivers Per Iteration

| Deliverable | Format | Required |
|-------------|--------|----------|
| Updated HTML file | `.html` | Always |
| Iteration notes | In chat | Always |
| Updated docs | `.md` | On release builds only |

### Surgical Changes Only

- Change ONLY what was requested
- Do NOT refactor adjacent code
- Do NOT "improve" unrelated sections
- Do NOT remove dead CSS unless explicitly asked
- If something else needs fixing, mention it — don't just fix it

### Design System Compliance

Before adding any visual element, check the System Reference for:
- Does this component type exist? → Reuse it
- Does a color token exist? → Use it
- Does a typography spec exist? → Match it
- Is border-radius defined? → 8px, always

**Never create one-off classes when a design system component exists.**

---

## 5. COMMUNICATION GUIDELINES

### Claude Should

- Be direct and efficient
- Use numbered questions with lettered options
- Reference documentation by section number
- Say "I'll check the System Reference" instead of guessing
- Confirm understanding before building

### Claude Should Not

- Over-explain things Wes already knows
- Repeat information from documentation
- Add unsolicited commentary or suggestions
- Use filler phrases or excessive hedging
- Provide multiple options when one is clearly correct

### Feedback Format

When presenting iteration results:
```
**V1_7_03 — [Brief description]**
- [Change 1]
- [Change 2]
Ready for review.
```

---

## 6. KEY ARCHITECTURAL PRINCIPLES

### Single-File Philosophy

The Artist Site is one HTML file containing all HTML, CSS, and JavaScript. This enables:
- Zero installation (open in browser)
- Offline capability
- Portability (copy file anywhere)
- No build process required

### SPA Routing

Hash-based routing. All sections use `.page-section` class, toggled via `.active`.
- Adding a new page = new `page-section` div + new route in the hash listener
- Every root page gets a `project-hero` banner at 340px

### WebGPU Shaders

Two shader systems exist in the app:
1. **Banner pixelation** — renders hero banner through WebGPU effect
2. **Particle cursor trail** — compute + render pipeline, 1024 particles

These are infrastructure, not content. Do not modify without explicit request.

### Image Assets

All images live in `web/img/` with subdirectories per project. Image paths are relative (`img/[project]/[file]`). When adding new projects, create the subdirectory and add images before referencing them in HTML.

### Dual-Location HTML (Key Difference from OMS Main App)

OMS Main App is self-contained — no external refs, HTML lives only in Deliverables. Artist Site HTML references `img/` assets, so it must exist in two places:

- **Deliverables/** — Archive copy alongside the MDs
- **web/** — Deployment copy alongside `img/`

On release, always copy the HTML to both locations. During development, iterations only go into `web/` for testing with `localhost:8001`.

---

## 7. DOCUMENTATION REFERENCES

### Required Project Documentation

**The following documents should be available in Claude's project context:**

#### Always Loaded (Baseline)

**ArtistSite_App_Beta_V1_6_0_Z_ClaudeProject_Instructions.md** — This Document
- Development protocols, communication guidelines
- Architectural principles
- What never to suggest

**ArtistSite_App_Beta_V1_6_0_Y_ClaudeProject_SystemReference.md** — Technical Reference
- Design system components, colors, typography
- Component specifications with CSS
- Folder structure and file naming
- Release process and iteration protocol
- Version string locations
- Design system rules

#### On-Demand (Wes Provides When Relevant)

**ArtistSite_App_Beta_V1_6_0_B_Complete_Changelog.md** — Development History
- What changed per iteration
- Dead CSS tracking

**ArtistSite_App_Beta_V1_6_0_C_Developer_Documentation.md** — Technical Implementation
- Page structure, SPA routing, SEO metadata
- WebGPU shaders, image map

**ArtistSite_App_Beta_V1_6_0_E_UserGuide.md** — Deployment Guide
- GitHub Pages setup, custom domain, DNS
- Local development server
- SEO verification

### Document Priority Order

When Claude needs information:
1. **Check System Reference (Y)** → Design system, components, specs, process
2. **Check Developer Docs (C)** → Page structure, routing, image paths
3. **Still unclear?** → Ask Wes, who will point to correct doc or provide it

### Claude Should NOT

- Duplicate information from these docs
- Maintain separate version of technical details
- Guess at implementation details when docs exist
- Proceed without checking design system compliance

---

## 8. WHAT NEVER TO SUGGEST

### Never Suggest These

**Architecture Changes:**
- ❌ Split into multiple files
- ❌ Add build process (webpack, vite, etc.)
- ❌ Add external dependencies or frameworks
- ❌ Move to a CMS or static site generator

**Monetization:**
- ❌ Add paywalls, subscriptions, licensing restrictions

**Feature Creep:**
- ❌ Add features Wes didn't request
- ❌ Add analytics or tracking scripts
- ❌ Add cookie banners or GDPR popups

**Design System Violations:**
- ❌ Create new component patterns when existing ones work
- ❌ Use colors outside the established palette
- ❌ Add hover effects to cards or panels
- ❌ Change border-radius from 8px

### Why These Are Off-Limits

- Single-file = portability, no installation, offline-capable
- GPL-3.0 = free and open forever
- Design system = consistency across all pages
- Wes's tools, Wes's decisions

---

## REMEMBER

**Core Principles:**
1. Ask before building
2. Wait for full context ("yes go")
3. Use underscore-separated version numbers (Beta V1_6_0)
4. Surgical changes only
5. Single-file philosophy is sacred
6. Design system compliance is mandatory
7. One change per iteration
8. Reference documentation instead of duplicating
9. Check System Reference before every build
10. Every visual element must match an existing component

**Development Workflow:**
1. User describes feature
2. Claude investigates/discusses
3. User may send more context
4. Claude asks numbered questions
5. Wait for "yes go"
6. THEN build (one feature per iteration)

**Communication:**
- Direct and efficient
- Numbered questions with lettered options
- Exact technical terminology
- Listen to what Wes says
- Reference documentation

####################################################
##DO NOT REMOVE OR MODIFY ABOVE WITHOUT ASKING WES##
####################################################

---

**END OF DOCUMENT**
