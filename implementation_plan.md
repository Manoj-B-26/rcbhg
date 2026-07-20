# Rotaract Club of HighGrounds — Immersive 3D Website

A cinematic, scroll-driven website with an OG Crew-inspired intro sequence, Indian-themed aesthetics, and Rotaract Club content structure.

## User Review Required

> [!IMPORTANT]
> **Opening Sequence**: The site opens with a fullscreen **Vidhana Soudha image** → morphs/zooms into the **club logo** → then reveals the main website. This is achieved through scroll-driven CSS transform animations (no heavy 3D library needed, using CSS `perspective`, `transform: scale3d`, and opacity transitions tied to scroll).

> [!IMPORTANT]
> **Font**: Using **Nasyahama** (Hindi Decorative Display Font) — I'll load it via `@font-face` from a local file. You'll need to provide the `.woff2`/`.ttf` file, or I can use a Google Fonts alternative that has a similar decorative Hindi feel. For now I'll set up the `@font-face` placeholder and use a fallback.

> [!IMPORTANT]
> **Images**: The provided `logo.jpg` and `vs.jpg` (Vidhana Soudha) will be used. I'll generate Indian-themed decorative assets (rangoli patterns, mandala borders, lotus motifs) using the image generation tool.

## Open Questions

> [!WARNING]
> 1. **Nasyahama font file** — Do you have the `.ttf`/`.woff2` file to include, or should I use a similar decorative font from Google Fonts (e.g., Yatra One, Tiro Devanagari Hindi)?
> 2. **Deployment** — Will this be deployed via GitHub Pages, Vercel, or a custom host? This affects the build approach.
> 3. **Single-page or multi-page?** — The reference site has About, Projects, Team, Brand Center pages. Should I create all as sections on a single page, or as separate HTML files?

## Proposed Changes

This will be a **static HTML/CSS/JS website** (no framework needed) with scroll-driven animations for the cinematic feel. The project structure:

---

### Core Structure

#### [NEW] [index.html](file:///c:/RCBHG/Website/rcbhg_v1/index.html)
The main HTML file containing the entire single-page website with these sections:
1. **Intro Sequence (Vidhana Soudha → Logo → Hero)** — Pinned fullscreen sections that animate on scroll
2. **Navigation** — Fixed glassmorphism navbar (appears after intro) with Indian decorative border
3. **Hero Section** — Club name with animated rangoli/mandala background patterns
4. **Quick Links Bar** — OG Crew-style buttons (About, Team, Projects, Events, Contact) with zoom-into effect
5. **About Section** — Club intro with Indian motif borders, placeholder text
6. **Focus Areas** — Rotary's 7 areas of focus with animated cards
7. **Projects Section** — Grid of project cards with hover animations
8. **Team Section** — Leadership gallery with circular photo frames and mandala borders
9. **Events Section** — Timeline-style upcoming events
10. **Stats Counter** — Animated counters (Members, Projects, Hours, etc.)
11. **Contact Section** — Contact form with social links
12. **Footer** — With Rotary/Rotaract branding and Indian decorative elements

#### [NEW] [styles.css](file:///c:/RCBHG/Website/rcbhg_v1/styles.css)
Complete design system with:
- **Color palette**: Deep Saffron (#FF9933), Indian Navy (#1A1A5E), Maroon (#800020), Gold (#D4AF37), Ivory (#FFFFF0), Teal (#1B4D4E)
- **CSS Custom Properties** for all design tokens
- **Indian-themed decorations**: Mandala SVG borders, rangoli patterns as CSS backgrounds, lotus motif dividers
- **Glassmorphism** for nav and cards
- **Animations**: `@keyframes` for all micro-interactions
- **Scroll-driven animations** using `animation-timeline: scroll()` with fallback
- **Responsive design** for mobile/tablet/desktop

#### [NEW] [script.js](file:///c:/RCBHG/Website/rcbhg_v1/script.js)
JavaScript for:
- **Scroll-driven intro sequence**: Vidhana Soudha → Logo morph → Hero reveal with parallax
- **OG Crew-style button zoom**: Click a nav button → camera zooms into that section with scale/perspective transform
- **Intersection Observer** for reveal-on-scroll animations
- **Animated counters** on scroll into view
- **Smooth scroll** with easing
- **Mobile hamburger menu** with slide-in drawer
- **Parallax effects** on Indian decorative elements
- **Particle effect** (floating golden particles/diyas)

### Indian Theme Assets

#### [NEW] [assets/](file:///c:/RCBHG/Website/rcbhg_v1/assets/)
- Generated mandala/rangoli pattern images
- SVG decorative borders (paisley, lotus)
- The provided `logo.jpg` and `vs.jpg` will be moved here

---

## Technical Approach

### Intro Sequence (Key Feature)
```
Scroll Position 0-30%: Vidhana Soudha fullscreen with parallax zoom
Scroll Position 30-50%: VS fades + scales → Club Logo morphs in at center
Scroll Position 50-70%: Logo shrinks to navbar corner → Hero section reveals
Scroll Position 70%+:  Normal website scroll begins
```

This uses **CSS `position: sticky`** with scroll-linked transforms via JS `IntersectionObserver` + `scroll` event. No heavy 3D library — pure CSS `transform: scale3d()` + `perspective()`.

### OG Crew-Style Button Zoom
When clicking a navigation button:
1. Button scales up to fill screen
2. Background transitions to section color
3. Camera "flies" into the section
4. Smooth deceleration at destination

### Indian Design Elements
- **Mandala/Rangoli patterns** as section dividers (CSS `clip-path` + SVG)
- **Lotus motif** section headers
- **Paisley borders** on cards
- **Diya/lamp floating particles** using CSS animations
- **Saffron → White → Green** gradient accents (tricolor inspiration)
- **Gold filigree** borders on buttons and cards

### Performance
- No heavy JS frameworks — vanilla JS only
- CSS animations hardware-accelerated (`transform`, `opacity`)
- Lazy loading for below-fold images
- `will-change` hints for animated elements

## Verification Plan

### Manual Verification
- Open in Chrome/Edge and test the full intro scroll sequence
- Verify all animations are smooth (60fps target)
- Test responsive layout at mobile/tablet/desktop breakpoints
- Verify the OG Crew-style button zoom interaction
- Check that Indian decorative elements render correctly
- Test navigation and smooth scroll behavior
