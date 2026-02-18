# Dark Premium Landing Page Style Skill

> A design system and component pattern library inspired by [getcalendarly.com](https://getcalendarly.com/). Use this to build any premium, dark-themed, Apple-inspired landing page — not a copy of Calendarly, but a site that shares the same visual DNA: pure black backgrounds, cinematic whitespace, scroll-triggered reveals, and a refined minimalist aesthetic.

---

## 1. TECH STACK & FOUNDATIONS

- **Framework**: Next.js (App Router) or any React meta-framework
- **Styling**: CSS Modules, Tailwind CSS, or any scoped styling approach
- **Fonts**: Vercel Geist Sans (primary) + Geist Mono (monospace accents) — or Inter / SF Pro as alternatives
- **Icons**: Lucide React or any stroke-based icon set (24×24 viewBox, never filled)
- **Images**: Responsive with modern formats (AVIF/WebP), lazy-loaded
- **Animations**: CSS transitions + scroll-triggered transforms via Intersection Observer (no heavy animation libraries)

---

## 2. DESIGN PHILOSOPHY

| Principle | Implementation |
|-----------|---------------|
| **Dark-first** | Pure black (#000000) background, everything built on darkness |
| **Apple-inspired** | Clean sans-serif type, generous whitespace, premium feel |
| **Minimalist** | Content-sparse sections, each section makes ONE point |
| **Cinematic** | Full-viewport hero, dramatic gradients, depth via shadows/glows |
| **High-trust** | Clean, confident copy; no clutter; quality signals through restraint |

---

## 3. COLOR PALETTE

```css
:root {
  /* Backgrounds */
  --bg-primary: #000000;
  --bg-surface: #0a0a0a;
  --bg-elevated: #111111;
  --bg-card: #1c1c1c;
  --bg-nav: rgba(0, 0, 0, 0.5);          /* glassmorphism base */

  /* Text */
  --text-primary: #ffffff;
  --text-secondary: rgba(255, 255, 255, 0.7);
  --text-tertiary: rgba(255, 255, 255, 0.5);
  --text-muted: rgba(255, 255, 255, 0.4);

  /* Accents — pick 2-3 accent colors, assign one per feature section */
  --accent-primary: #f43f5e;              /* rose — use for primary feature section label + checkmarks */
  --accent-secondary: #3b82f6;            /* blue — use for secondary feature section label + checkmarks */
  --accent-tertiary: #f59e0b;             /* amber — use sparingly for warm icon glows or highlights */
  --accent-success: #22c55e;              /* green — optional, for positive/sync/success accents */

  /* Borders */
  --border-subtle: rgba(255, 255, 255, 0.05);
  --border-light: rgba(255, 255, 255, 0.1);
  --border-rim: rgba(255, 255, 255, 0.15);

  /* Shadows & Glows */
  --glow-white: rgba(255, 255, 255, 0.2);
  --glow-rose: #f43f5e90;
  --glow-amber: #f59e0b90;
  --shadow-deep: rgba(0, 0, 0, 0.4);
}
```

### Color Usage Rules
- **Backgrounds**: Always pure black or near-black. Never use gray backgrounds.
- **Accents**: Used sparingly — section labels, checkmark icons, floating card glows. Never for large fills.
- **Section-specific accent colors**: Each feature section uses ONE accent color for its label text AND its checkmark icons. Keep consistent within a section, vary between sections.
- **Text hierarchy**: White → 70% white → 50% white → 40% white (4 levels max).
- **Borders**: Always transparent or near-invisible (5-15% white opacity).

---

## 4. TYPOGRAPHY

```css
/* Font Stack */
font-family: 'Geist', system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif;
font-family: 'Geist Mono', ui-monospace, monospace; /* for code/technical text */

/* Type Scale */
.hero-headline {
  font-size: clamp(2.5rem, 5vw, 4.5rem);    /* ~40-72px */
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  color: #ffffff;
}

.section-headline {
  font-size: clamp(2rem, 4vw, 3.5rem);       /* ~32-56px */
  font-weight: 700;
  line-height: 1.15;
  letter-spacing: -0.02em;
  color: #ffffff;
}

.subheadline {
  font-size: clamp(1rem, 2vw, 1.25rem);      /* ~16-20px */
  font-weight: 400;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.7);
  max-width: 520px;
}

.section-label {
  font-size: 0.875rem;                        /* 14px */
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--section-accent);
  /* Each section gets its own accent color for this label */
  /* Displayed as uppercase colored text above the section headline */
}

.nav-link {
  font-size: 0.875rem;
  font-weight: 400;
  color: rgba(255, 255, 255, 0.7);
  transition: color 0.2s ease;
}

.nav-link:hover {
  color: #ffffff;
}

.feature-item {
  font-size: 0.9375rem;                      /* 15px */
  font-weight: 400;
  color: rgba(255, 255, 255, 0.8);
}

.footer-link {
  font-size: 0.875rem;
  font-weight: 400;
  color: rgba(255, 255, 255, 0.5);
}

.footer-column-header {
  font-size: 0.75rem;                        /* 12px */
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: rgba(255, 255, 255, 0.4);
}
```

### Typography Rules
- **Headline font-weight**: Always 700 (bold). Never light/thin for headers.
- **Negative letter-spacing** on headlines (`-0.02em`) for tight, modern look.
- **Line-height**: 1.1 for headlines, 1.6 for body text.
- **Max-width**: Body text paragraphs capped at ~520px for readability.
- **No ALL-CAPS** except section labels and footer column headers.

---

## 5. SPACING SYSTEM

```css
/* Spacing Scale (8px base) */
--space-1: 4px;
--space-2: 8px;
--space-3: 12px;
--space-4: 16px;
--space-5: 20px;
--space-6: 24px;
--space-8: 32px;
--space-10: 40px;
--space-12: 48px;
--space-16: 64px;
--space-20: 80px;
--space-24: 96px;
--space-32: 128px;

/* Section Padding */
section { padding: 120px 0; }               /* generous vertical breathing room */
.container { max-width: 1200px; margin: 0 auto; padding: 0 24px; }

/* Nav Padding */
nav { padding: 16px; gap: 96px; }           /* wide gap between logo and links */
```

### Spacing Rules
- **Sections**: Very generous vertical padding (100-140px top/bottom).
- **Between headline and subtext**: ~20-24px.
- **Between subtext and CTA**: ~32-40px.
- **Feature list items**: ~12-16px gap.
- **Content max-width**: 1200px container, 520px for text blocks.

---

## 6. COMPONENT SPECIFICATIONS

### 6.1 Navigation Bar

```
┌──────────────────────────────────────────────────────────┐
│  [Logo] AppName          Link 1   Link 2       [● CTA]  │
└──────────────────────────────────────────────────────────┘
```

**Styles:**
```css
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 50;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px;
  gap: 96px;
  background-color: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-color: transparent;
  transition: all 0.3s ease;
}
```

**Key details:**
- Logo: Small icon (32×32) + app name text
- Nav links: Centered, subtle white (70% opacity), brighten to 100% on hover
- CTA button: White pill, small variant (see §6.3)
- Glassmorphism: Semi-transparent black + `backdrop-filter: blur(12px)`
- Border becomes visible on scroll (subtle 1px white border-bottom at ~5% opacity)
- Max 2-3 nav links + 1 CTA — never cluttered

---

### 6.2 Hero Section

```
┌──────────────────────────────────────────────────────────┐
│                                                          │
│               [Bold Headline Here.]                      │
│                                                          │
│       One-liner subtitle describing the product          │
│         in clear, benefit-driven language.                │
│                                                          │
│                  [ ● Primary CTA ]                       │
│                                                          │
│          ┌─────────────────────────────┐                 │
│          │                             │                 │
│          │     Large Visual Showcase   │                 │
│          │   (product screenshots,     │                 │
│          │    mockups, or animation)   │                 │
│          │                             │                 │
│          └─────────────────────────────┘                 │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

**Structure:**
1. **Text Block** (centered above visual):
   - H1 headline: Large, bold, white — short and punchy
   - Subtitle paragraph: Secondary text color, 1-2 lines max
   - CTA button: Large variant with optional icon + white glow shadow

2. **Visual Block** (below text, centered):
   - A dramatic visual showcase of the product — this can be:
     - A grid/marquee of scrolling screenshots
     - A single large device mockup
     - An animated product demo
     - A 3D render or illustration
   - Edges should fade to black via gradient vignette overlays (top, bottom, left, right)
   - The visual is the hero's "wow factor" — make it cinematic

**Marquee pattern** (if using scrolling columns):
```css
/* Multiple vertical columns of images, adjacent columns scroll opposite directions */
@keyframes scrollUp {
  0% { transform: translateY(0); }
  100% { transform: translateY(-50%); }
}
@keyframes scrollDown {
  0% { transform: translateY(-50%); }
  100% { transform: translateY(0); }
}
.column:nth-child(odd) .content { animation: scrollUp 40s linear infinite; }
.column:nth-child(even) .content { animation: scrollDown 40s linear infinite; }
/* Duplicate content inside each column for seamless loop */
```

**Entry Animations:**
```css
/* Headline fades up */
.headline { opacity: 0; transform: translateY(30px); }
.headline.visible { opacity: 1; transform: translateY(0); transition: all 0.8s ease; }

/* Subtitle fades up (shorter distance) */
.subheadline { opacity: 0; transform: translateY(20px); }

/* CTA scales in */
.cta { opacity: 0; transform: scale(0.9); }
```

---

### 6.3 CTA / Download Button

**Two variants:**

**Large (hero):**
```css
.ctaButton {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  padding: 14px 28px;
  background: #ffffff;
  color: #000000;
  border-radius: 9999px;        /* full pill */
  font-size: 1rem;
  font-weight: 600;
  text-decoration: none;
  box-shadow: 0 0 50px rgba(255, 255, 255, 0.2);
  transition: transform 0.2s ease;
}
.ctaButton:hover {
  transform: scale(1.05);
}
.ctaButton .icon {
  width: 20px;
  height: 20px;
}
```

**Small (navbar):**
```css
.ctaSmall {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: #ffffff;
  color: #000000;
  border-radius: 9999px;
  font-size: 0.875rem;
  font-weight: 500;
}
```

**Footer variant:**
```css
.ctaFooter {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 32px;
  background: #ffffff;
  color: #000000;
  border-radius: 12px;          /* rounded-lg, NOT pill */
  font-size: 1rem;
  font-weight: 600;
}
```

---

### 6.4 Centered Feature Section

A standalone section for highlighting a single key feature with centered layout.

```
┌──────────────────────────────────────────────────────────┐
│                                                          │
│              [Section Headline.]                         │
│              [Second Line.]                              │
│                                                          │
│          Short centered subtitle text here.              │
│                                                          │
│      [icon]       ┌────────┐       [icon]                │
│                   │ visual │                             │
│                   │        │                             │
│                   └────────┘                             │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

**Structure:**
- **Centered headline + subtitle** using standard `section-headline` + `subheadline` styles
- **Single centered visual** below (product mockup, illustration, or graphic)
- **Optional floating icon cards** flanking the visual — one on each side, slightly offset
  - Each icon card uses a different accent glow color
- Good for features that don't need a bullet list — just a statement + visual proof

```css
.centeredSection {
  padding: 120px 0;
  text-align: center;
  position: relative;
}
.centeredVisual {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 48px;
  gap: 40px;
}
```

---

### 6.5 Two-Column Feature Section

**Reusable pattern for each major feature. Alternate text/visual sides.**

```
┌──────────────────────────────────────────────────────────┐
│                                                          │
│   SECTION LABEL                ┌────────────────────┐   │
│                                │                    │   │
│   Headline Text.               │   Visual / Image   │   │
│   Second Line.                 │   or Mockup         │   │
│                                │                    │   │
│   Body paragraph explaining    │                    │   │
│   the feature briefly.         └────────────────────┘   │
│                                                          │
│   ✓ Benefit point one                                    │
│   ✓ Benefit point two                                    │
│   ✓ Benefit point three                                  │
│   ✓ Benefit point four                                   │
│   ✓ Benefit point five                                   │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

**Key pattern rules:**
- Each section has: colored label → bold headline → body text → checkmark list → visual
- **Alternate layout direction**: first section = text-left/visual-right, next = visual-left/text-right
- The label and checkmark icons share the same accent color (unique per section)
- 4-6 bullet points per feature, each 2-5 words

**Structure:**
```css
.section {
  padding: 120px 0;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  gap: 64px;
}
/* Alternate: privacy section reverses order (image left, text right) */
```

**Label (above headline):**
```css
.label {
  display: inline-block;
  font-size: 0.875rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--section-accent);          /* accent color matching this section */
  margin-bottom: 16px;
}
```

**Feature checklist (checkmark icons use same accent color as label):**
```css
.featureItem {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 0.9375rem;
  color: rgba(255, 255, 255, 0.8);
}
.featureItem svg {
  width: 20px;
  height: 20px;
  stroke: var(--section-accent);         /* matches section label color */
  stroke-width: 2;
  flex-shrink: 0;
}
```

**Scroll-in animations:**
```css
/* Content side slides from left */
.contentSide { opacity: 0; transform: translateX(-30px); }
/* Visual side slides from right */
.visualSide { opacity: 0; transform: translateX(30px); }
/* Each feature item staggers in */
.featureItem { opacity: 0; transform: translateX(-20px); }
```

---

### 6.6 Floating Icon Cards

Floating 3D-styled icon cards used as decorative accents around visuals:

```css
.floatingElement {
  position: absolute;
  animation: float 6s ease-in-out infinite;
}

.iconCard {
  width: 76px;
  height: 76px;
  border-radius: 20px;
  position: relative;
  background: linear-gradient(145deg, #1c1c1c, #111111);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  box-shadow:
    0 0 0 1px rgba(255, 255, 255, 0.05),        /* outer definition */
    inset 1px 1px 0px rgba(255, 255, 255, 0.15), /* rim light */
    0 10px 20px rgba(0, 0, 0, 0.4),              /* drop shadow */
    0 0 40px -5px var(--accent-glow);             /* colored aura */
}

/* Noise texture overlay */
.iconCard::before {
  content: '';
  position: absolute;
  inset: 0;
  opacity: 0.1;
  background-image: url("data:image/svg+xml,...fractalNoise...");
  pointer-events: none;
}

/* Top shine */
.iconCard::after {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 50%;
  background: linear-gradient(180deg, rgba(255,255,255,0.03) 0%, transparent 100%);
  pointer-events: none;
}

/* Icon styling */
.iconCard svg {
  z-index: 1;
  width: 32px;
  height: 32px;
  stroke: var(--accent-color);
  filter: drop-shadow(0 1px 0 rgba(255,255,255,0.2)) drop-shadow(0 0 5px var(--accent-color));
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}
```

---

### 6.7 Footer

```
┌──────────────────────────────────────────────────────────┐
│             [Closing CTA headline question?]             │
│                   [Subtle subtitle]                      │
│                  [ ● Download CTA ]                      │
│                                                          │
│  ─────────────────────────────────────────────────────── │
│                                                          │
│  Column 1        Column 2           Column 3             │
│  Link             Link               Link                │
│  Link             Link               Link                │
│  Link                                                    │
│                                                          │
│  © 2026 Company.                              [socials]  │
└──────────────────────────────────────────────────────────┘
```

```css
.footer {
  background: #000000;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.ctaSection {
  text-align: center;
  padding: 80px 24px 60px;
}

.ctaTitle {
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 8px;
}

.ctaSubtitle {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.5);
  margin-bottom: 32px;
}

.divider {
  height: 1px;
  background: rgba(255, 255, 255, 0.05);
  margin: 0 24px;
}

.columnsGrid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 48px;
  padding: 48px 24px;
}

.columnHeader {
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: rgba(255, 255, 255, 0.4);
  margin-bottom: 16px;
}

.bottomBar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 24px;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
}

.copyright {
  font-size: 0.8125rem;
  color: rgba(255, 255, 255, 0.3);
}

.socialIcon {
  width: 20px;
  height: 20px;
  fill: rgba(255, 255, 255, 0.4);
  transition: fill 0.2s ease;
}
.socialIcon:hover {
  fill: #ffffff;
}
```

---

## 7. ANIMATION PATTERNS

### 7.1 Scroll-Triggered Fade-In
Every section element starts invisible and animates in on scroll:

```css
/* Initial state */
[data-animate] {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}

/* Visible state */
[data-animate].visible {
  opacity: 1;
  transform: translateY(0);
}
```

**Directions used:**
- Headlines: `translateY(30px)` → 0
- Subtitles: `translateY(20px)` → 0
- CTAs: `scale(0.9)` → 1
- Left content: `translateX(-30px)` → 0
- Right content: `translateX(30px)` → 0
- Feature items: `translateX(-20px)` → 0 (staggered 100ms each)

### 7.2 Marquee Scrolling Columns
```css
@keyframes scrollUp {
  0% { transform: translateY(0); }
  100% { transform: translateY(-50%); }
}
@keyframes scrollDown {
  0% { transform: translateY(-50%); }
  100% { transform: translateY(0); }
}

.marqueeColumn .marqueeContent {
  animation: scrollUp 40s linear infinite;
}
.marqueeColumn:nth-child(even) .marqueeContent {
  animation: scrollDown 40s linear infinite;
}
```
Content is **duplicated** inside each column to create seamless loop.

### 7.3 Hover Effects
```css
/* CTA buttons */
.ctaButton:hover { transform: scale(1.05); }

/* Nav links */
.navLink:hover { color: #ffffff; }

/* Footer links */
.footerLink:hover { color: rgba(255, 255, 255, 0.8); }
```

---

## 8. GRADIENT & OVERLAY RECIPES

### Vignette Overlays (fade edges of visual sections to black)
```css
.gradientTop {
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 200px;
  background: linear-gradient(to bottom, #000000, transparent);
  z-index: 2;
  pointer-events: none;
}
.gradientBottom {
  position: absolute;
  bottom: 0; left: 0; right: 0;
  height: 200px;
  background: linear-gradient(to top, #000000, transparent);
  z-index: 2;
  pointer-events: none;
}
.vignetteLeft {
  position: absolute;
  top: 0; bottom: 0; left: 0;
  width: 200px;
  background: linear-gradient(to right, #000000, transparent);
  z-index: 2;
  pointer-events: none;
}
.vignetteRight {
  position: absolute;
  top: 0; bottom: 0; right: 0;
  width: 200px;
  background: linear-gradient(to left, #000000, transparent);
  z-index: 2;
  pointer-events: none;
}
```

### Glow Background (accent glow behind visuals)
```css
.glowBackground {
  position: absolute;
  width: 400px;
  height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(244, 63, 94, 0.15), transparent 70%);
  filter: blur(60px);
  pointer-events: none;
}
```

---

## 9. RESPONSIVE BREAKPOINTS

```css
/* Mobile-first approach */
@media (max-width: 768px) {
  /* Stack two-column layouts vertically */
  .container { flex-direction: column; }

  /* Hero headline smaller */
  .headline { font-size: 2.5rem; }

  /* Reduce section padding */
  section { padding: 80px 0; }

  /* Show only 3 marquee columns (hide outer ones) */
  .colOuter { display: none; }

  /* Nav: show hamburger menu */
  .desktopNav { display: none; }

  /* Footer grid: single column */
  .columnsGrid { grid-template-columns: 1fr; }
}

@media (max-width: 480px) {
  .headline { font-size: 2rem; }
  section { padding: 60px 0; }
}
```

---

## 10. PAGE STRUCTURE (Recommended Section Order)

1. **Header** — Fixed glassmorphism nav (logo + links + CTA pill)
2. **Hero** — Centered headline + subtitle + CTA + dramatic visual showcase
3. **Centered Feature** — Single key feature with centered text + flanking visuals
4. **Two-Column Feature A** — Text left, visual right (with accent color A)
5. **Two-Column Feature B** — Visual left, text right (with accent color B)
6. **Footer** — Closing CTA + divider + link columns + copyright bar

**Notes:**
- You can add more centered or two-column sections as needed — just maintain the alternating left/right pattern
- Each section should make exactly ONE point
- Keep total sections to 4-6 for a landing page (not counting header/footer)

---

## 11. IMPLEMENTATION CHECKLIST

When recreating this style for a new product:

- [ ] Set `<html>` and `<body>` background to `#000000`
- [ ] Install Geist font (`@vercel/font` or Google Fonts fallback)
- [ ] Apply `antialiased` class to body
- [ ] Build nav with glassmorphism (`backdrop-filter: blur(12px)`)
- [ ] Use CSS Modules for scoped styles (or Tailwind with dark defaults)
- [ ] Hero: Centered text block above a visual showcase
- [ ] All text sections: label → headline → subtitle → feature list
- [ ] Feature lists use Lucide `Check` icon (20×20, stroke-based)
- [ ] Two-column sections alternate direction (text-left/text-right)
- [ ] Every element starts invisible and fades in on scroll
- [ ] Stagger feature item animations by ~100ms
- [ ] CTA buttons: white pill, black text, scale on hover
- [ ] Large CTA: white glow shadow (`0 0 50px rgba(255,255,255,0.2)`)
- [ ] Vignette gradients on visual section edges
- [ ] Footer: centered CTA section → divider → column grid → copyright bar
- [ ] All transitions: `0.2-0.8s ease` (never bounce/spring)
- [ ] Icons: stroke-only Lucide icons, never filled

---

## 12. COPY TONE & VOICE

- **Headlines**: Short, punchy, 2-6 words. Period or no punctuation. Declarative statements.
- **Subheadlines**: One sentence, benefits-focused, elegant. No jargon or buzzwords.
- **Section labels**: Uppercase, 2-4 words. Describe the feature category.
- **Feature bullet items**: 2-5 words each, noun phrases. Start with the benefit.
- **CTA text**: Action-oriented but understated. ("Get started", "Try it free", "Download now")
- **Footer CTA**: Question format inviting the user to act. ("Ready to [benefit]?")
- **Overall tone**: Confident, clean, direct. Reads like Apple marketing — never salesy or loud.

---

## 13. DO's AND DON'Ts

### DO ✅
- Use pure black backgrounds
- Keep generous whitespace between sections (100px+)
- Use white text with opacity levels for hierarchy
- Apply subtle glow/shadow on floating elements
- Animate elements on scroll (fade + translate)
- Use pill-shaped CTAs with white background
- Keep nav minimal (logo + 2-3 links + CTA)

### DON'T ❌
- Use any gray backgrounds (keep to #000 or very near-black #0a0a0a)
- Use colored backgrounds for sections
- Apply borders heavier than 1px / 10% opacity white
- Use gradient text (keep text solid white)
- Add too many nav items (max 3 links + CTA)
- Use filled icons (always stroke-based)
- Use bouncy/springy animations (keep to ease curves)
- Add loading spinners or skeleton screens (instant or fade-in only)
- Use shadows on text (only on icon cards/floating elements)
