# DESIGN.md — John's Schoonmaakbedrijf

> **Source of truth for all design tokens and decisions.**
> Read this before making ANY visual decision during the build phase.
> For layout intent, cross-reference `homepage-reference.html`.

---

## 1. Project Identity

| Field | Value |
|---|---|
| **Client name** | John's Schoonmaakbedrijf |
| **Business type** | Schoonmaakbedrijf — kantoorschoonmaak (B2B primary) |
| **Archetype** | E — Lifestyle & Personal Brand (schoonmaakbedrijf sub-type) |
| **Sub-variant** | B2B: kantoorschoonmaak voor bedrijven |
| **Owner** | John Hak |
| **Business address** | Buren, Gelderland |
| **Operational base** | Tricht (vestigingsplaats — historical) |
| **Region framing** | Betuwe (primary SEO region), Rivierenland (secondary) |
| **Service area** | Betuwe & Rivierenland |

### Visual tone scores

| Dimension | Score | Notes |
|---|---|---|
| Energy | 7/10 | Active, confident — not corporate flat |
| Density | 5/10 | Balanced — not sparse, not cluttered |
| Formality | 6/10 | Bumped from archetype default (5) for B2B sub-variant |
| Richness | 6/10 | Multiple visual layers, restrained luxury |
| Animation | 5/10 | CSS-only, hover states + scroll reveals |

### Brand assets

| Asset | Status | Decision |
|---|---|---|
| Logo | Available (`logo(1).png` in root) | Use in nav + footer |
| Brand colors | Not defined by client | Chose Palette D "Energiek Schoon" |
| Brand fonts | Not defined by client | Chose Outfit + Inter |

### Addressal

**u / uw** — resolved 2026-04-18 based on voice extraction from John Hak's historical copy (CLIENT-VOICE.md + CONTENT-SOURCE.md). John's entire 19-year body of work uses `u/uw` consistently, on both johnsglazenwassersbedrijf.nl and johnsschoonmaakbedrijf.nl, across service pages, location pages, the fake-news defense post, and even the rolluiken Facebook one-liners. He uses `je` ONLY in job ads (recruitment context) — a register shift that is sector-normal and doesn't apply to customer-facing copy. The "approachable" personality is carried via word choice (`gerust`, `graag`, `wel`, `alles is mogelijk`, `net anders`) rather than pronoun register. Maintain `u/uw` consistently throughout all copy and UI microcopy. This overrides the general user CLAUDE.md preference for `je/jij`.

### Target audience

Facility managers, office managers, and business owners in Betuwe & Rivierenland seeking reliable, certified commercial cleaning. Decision driver: trust + professionalism. Price is secondary to reliability.

---

## 2. Color System

All values extracted from `homepage-reference.html` `:root` block.

| Role | CSS Variable | Hex | WCAG on white | Usage |
|---|---|---|---|---|
| **Primary** | `--c-primary` | `#0369A1` | 5.93:1 AA | Buttons, links, icons, borders, focus rings |
| **Primary light** | `--c-primary-light` | `#0EA5E9` | 3.00:1 AA large | Gradients, hover accents, timeline step 2 |
| **Primary 50** | `--c-primary-50` | `#F0F9FF` | — | Certs strip bg, very light accent tint |
| **Primary 100** | `--c-primary-100` | `#E0F2FE` | — | Icon wrappers, trust icon bg, badge bg |
| **Accent** | `--c-accent` | `#FACC15` | 11.66:1 AAA on navy | Floating badge, stars, footer badges, service tag |
| **Accent dark** | `--c-accent-dark` | `#EAB308` | — | Accent hover state |
| **Navy** | `--c-navy` | `#0F172A` | — | Dark section bg (reviews, footer), headings, dark card |
| **Navy 800** | `--c-navy-800` | `#1E293B` | — | Secondary dark (reserved) |
| **Background** | `--c-bg` | `#FFFFFF` | — | Page bg, white sections (hero, werkwijze, contact) |
| **Surface** | `--c-surface` | `#F9FAFB` | — | Light section bg (services, over ons), card bg |
| **Surface blue** | `--c-surface-blue` | `#EFF6FF` | — | USP strip bg, certs strip bg |
| **Text** | `--c-text` | `#0F172A` | 18.06:1 AAA | All body text on white/surface |
| **Text muted** | `--c-text-muted` | `#4B5563` | 7.45:1 AAA | Secondary text, card body, sub-headings |
| **Text light** | `--c-text-light` | `#9CA3AF` | 3.05:1 AA large | Captions, labels, form hints |
| **Border** | `--c-border` | `#E5E7EB` | — | Card borders, dividers, form fields |
| **Border light** | `--c-border-light` | `#F3F4F6` | — | Subtle separators |

### Section background sequence (never repeat adjacent)

1. Hero → `#FFFFFF` (white)
2. USP Strip → `#EFF6FF` (surface-blue)
3. Services → `#F9FAFB` (surface)
4. Werkwijze → `#FFFFFF` (white)
5. Reviews → `#0F172A` (navy — dark section)
6. Over Ons → `#F9FAFB` (surface)
7. Certs → `#F0F9FF` (primary-50)
8. Contact → `#FFFFFF` (white)
9. Footer → `#0F172A` (navy)

---

## 3. Typography

### Font families

```css
--font-head: 'Outfit', system-ui, sans-serif;
--font-body: 'Inter', system-ui, sans-serif;
```

### Google Fonts import

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700;800&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

Use `display=swap` (already in URL) to prevent FOIT.

### Type scale

| Level | Font | Size | Weight | Line-height | Letter-spacing | Usage |
|---|---|---|---|---|---|---|
| **H1** | Outfit | `clamp(42px, 4vw, 62px)` | 800 | 1.08 | -0.025em | Hero only |
| **H2** | Outfit | `clamp(28px, 2.5vw, 40px)` | 700 | 1.15 | -0.02em | Section headings |
| **H3 anchor** | Outfit | `30px` | 800 | 1.2 | -0.02em | Dark anchor service card |
| **H3 card** | Outfit | `18–19px` | 700 | — | — | Regular service cards, steps |
| **Kicker** | Outfit | `11px` | 700 | — | `2–2.5px` | Section labels, uppercase |
| **Body large** | Inter | `17px` | 400 | 1.7 | — | Hero sub, over-ons body |
| **Body** | Inter | `16px` | 400 | 1.75 | — | Standard body copy |
| **Body small** | Inter | `14–15px` | 400 | 1.6–1.65 | — | Card text, form body |
| **Caption** | Inter | `12–13px` | 500–600 | — | — | Labels, badges, meta |
| **Review score** | Outfit | `80px` | 900 | 1 | -0.04em | Reviews section big number |
| **Nav link** | Inter | `14px` | 500 | — | — | Navigation |
| **Footer col title** | Outfit | `13px` | 700 | — | `1.5px` | Footer nav headings, uppercase |
| **Button** | Outfit | `15px` | 600 | — | — | All CTA buttons |
| **Button sm** | Outfit | `13px` | 600 | — | — | Nav CTA, small buttons |

### Responsive type overrides

```css
@media (max-width: 480px) {
  .hero-h1 { font-size: 36px; }
  .section-heading { font-size: 26px; }
  .score-big { font-size: 64px; }
}
```

### Dutch hyphens

Apply `hyphens: auto` and `lang="nl"` on `<html>` element — essential for long compound words (kantoorschoonmaak, schoonmaakdiensten).

---

## 4. Spacing System

### Container

```css
--container: 1360px;
max-width: var(--container);
margin-inline: auto;
padding-inline: 40px;  /* 20px on ≤768px */
```

### Section padding (intentionally varied — do NOT normalize)

| Section | Padding |
|---|---|
| Hero | `pt: 80px, pb: 64px` |
| USP strip | `py: 48px` |
| Services | `pt: 80px, pb: 96px` |
| Werkwijze | `pt: 80px, pb: 112px` |
| Reviews | `py: 96px` |
| Over Ons | `pt: 64px, pb: 96px` |
| Certs | `py: 40px` |
| Contact | `py: 96px` |
| Footer | `pt: 64px, pb: 32px` |

At `≤768px`: hero → `48px 0 48px`, services/werkwijze → `60px 0 72px`, reviews → `64px 0`, over-ons → `48px 0 64px`, contact → `64px 0`.

### Grid gaps

| Context | Gap |
|---|---|
| Hero grid | `64px` |
| Services grid | `20px` |
| Timeline | `32px` |
| Review cards | `20px` |
| Over Ons grid | `80px` |
| Reviews top split | `64px` |
| Contact grid | `64px` |
| Footer grid | `48px` |
| USP items | `0` (border-right separators) |

### Border radius tokens

```css
--r-sm:   6px;   /* chips, small badges */
--r-md:   12px;  /* contact methods, form fields, icon wrappers */
--r-lg:   20px;  /* cards (service, review, step), form wrap container */
--r-xl:   28px;  /* hero image, service anchor card, contact form wrap */
--r-full: 9999px; /* all pill buttons, all badge chips */
```

### Shadow tokens

```css
--shadow-sm:   0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04);
--shadow-card: 0 4px 16px rgba(3,105,161,0.08), 0 1px 4px rgba(0,0,0,0.04);
--shadow-lift: 0 12px 40px rgba(3,105,161,0.16), 0 4px 12px rgba(0,0,0,0.08);
--shadow-btn:  0 4px 16px rgba(3,105,161,0.35);
```

### Component internal padding

| Component | Padding |
|---|---|
| Button primary/accent | `14px 28px` |
| Button secondary | `13px 28px` (2px border offset) |
| Button small | `10px 20px` |
| Service card | `28px` |
| Service anchor card | `44px 44px 40px` |
| Review card | `28px` |
| Step card | `24px` |
| Contact form wrap | `36px` |
| Contact method row | `16px` |
| Float card | `18px 22px` |
| Owner profile | `20px` |
| Stat block | `20px 16px` |
| Nav height | `72px` |
| Certs badge icon | `52px × 52px` |

---

## 5. Component Styles

### Buttons

**Primary (`.btn-primary`)**
```css
background: #0369A1;
color: #fff;
border-radius: 9999px;
padding: 14px 28px;
font-family: Outfit; font-size: 15px; font-weight: 600;
/* hover: */ background: #0F172A; box-shadow: 0 4px 16px rgba(3,105,161,0.35); transform: translateY(-1px);
```

**Secondary/Ghost (`.btn-secondary`)**
```css
background: transparent;
color: #0369A1;
border: 2px solid #0369A1;
border-radius: 9999px;
padding: 13px 28px;
/* hover: */ background: #0369A1; color: #fff;
```

**Accent (`.btn-accent`)**
```css
background: #FACC15;
color: #0F172A;
font-weight: 700;
border-radius: 9999px;
padding: 14px 28px;
/* hover: */ background: #EAB308; transform: translateY(-1px); box-shadow: 0 6px 20px rgba(234,179,8,0.4);
```

**Ghost white (`.btn-ghost-white`)** — for dark section backgrounds
```css
background: transparent;
color: rgba(255,255,255,0.9);
border: 2px solid rgba(255,255,255,0.35);
border-radius: 9999px;
/* hover: */ border-color: rgba(255,255,255,0.7); color: #fff;
```

All buttons: `transition: all 0.2s`

### Cards

**Service card (`.service-card`)**
```css
background: #FFFFFF;
border-radius: 20px;
border: 1px solid #E5E7EB;
box-shadow: var(--shadow-card);
padding: 28px;
transition: box-shadow 0.25s, transform 0.25s;
/* hover: */ box-shadow: var(--shadow-lift); transform: translateY(-4px);
```

**Service anchor card (`.service-anchor`)** — dark dominant card
```css
background: #0F172A;
border-radius: 28px;
padding: 44px 44px 40px;
min-height: 420px;
```

**Review card (`.review-card`)**
```css
background: rgba(255,255,255,0.07);
border: 1px solid rgba(255,255,255,0.12);
border-radius: 20px;
padding: 28px;
transition: background 0.2s;
/* hover: */ background: rgba(255,255,255,0.11);
```

### Form fields

```css
/* Input, Select, Textarea */
background: #FFFFFF;
border: 1px solid #E5E7EB;
border-radius: 12px;
padding: 12px 14px;
font-family: Inter; font-size: 14px;
transition: border-color 0.2s, box-shadow 0.2s;
/* focus: */ border-color: #0369A1; box-shadow: 0 0 0 3px rgba(3,105,161,0.12);
```

Form is wrapped in a surface-bg card (`background: #F9FAFB`, `border-radius: 28px`, `padding: 36px`, `border: 1px solid #E5E7EB`).

Label: `font-size: 13px; font-weight: 600; color: #0F172A`

### Badges and pills

**Section kicker** — uppercase label above section headings
```css
display: inline-block;
font-family: Outfit; font-size: 11px; font-weight: 700;
text-transform: uppercase; letter-spacing: 2.5px;
color: #0369A1;
margin-bottom: 10px;
```

**Hero eyebrow pill**
```css
font-size: 11px; font-weight: 700; text-transform: uppercase; letter-spacing: 2px;
color: #0369A1; background: #E0F2FE;
border: 1px solid #BAE6FD;
padding: 5px 14px; border-radius: 9999px;
/* has ::before dot: 6px circle, #0EA5E9 */
```

**Service tag (on dark card)**
```css
font-size: 10px; font-weight: 700; text-transform: uppercase; letter-spacing: 2px;
color: #FACC15; background: rgba(250,204,21,0.15);
border: 1px solid rgba(250,204,21,0.3);
padding: 4px 12px; border-radius: 9999px;
```

**Step badge (timeline)**
```css
font-size: 12px; font-weight: 600;
color: #0369A1; background: #E0F2FE;
border: 1px solid #BAE6FD;
padding: 3px 12px; border-radius: 9999px;
```

**Footer badge**
```css
font-size: 10px; font-weight: 700; text-transform: uppercase; letter-spacing: 1px;
color: #FACC15; background: rgba(250,204,21,0.12);
border: 1px solid rgba(250,204,21,0.2);
padding: 4px 10px; border-radius: 9999px;
```

### Navigation

```css
/* Nav bar */
position: sticky; top: 0; z-index: 100;
background: #FFFFFF; border-bottom: 1px solid #E5E7EB;
height: 72px;

/* Nav links */
font-size: 14px; font-weight: 500; color: #4B5563;
transition: color 0.2s;
/* hover/active: */ color: #0369A1;

/* Nav phone */
font-size: 14px; font-weight: 600; color: #4B5563;
transition: color 0.2s;
/* hover: */ color: #0369A1;
```

At ≤768px: nav links and phone are hidden (`display: none`).

---

## 6. Grid & Layout

### Grid structures per section

| Section | Columns (desktop) | Notes |
|---|---|---|
| Hero | `58fr 42fr` | 60/40 split, gap 64px |
| USP strip | `repeat(3, 1fr)` | Border-right separators, no gap |
| Services | `5fr 3fr`, anchor `grid-row: span 2` | Editorial asymmetric, L2 pattern |
| Werkwijze | `repeat(3, 1fr)` | Gap 32px, connector line overlay |
| Reviews top | `3fr 5fr` | Score left, heading/testimonial right |
| Review cards | `repeat(3, 1fr)` | Gap 20px |
| Over Ons | `7fr 5fr` | Gap 80px, image right |
| Certs | `flex row, space-between` | Flex wrap, label + badges |
| Contact | `5fr 4fr` | Info left, form right |
| Footer | `2fr 1fr 1fr 1fr` | Brand col wider, gap 48px |

### Breakpoints

**≤1024px (tablet)**
- Hero: stacks to `1fr` (single column)
- Hero float card + badge: hidden
- USP strip: stacks to `1fr` (border-bottom separators replace border-right)
- Services: stacks to `1fr` (anchor card `grid-row: span 1`, min-height 320px)
- Timeline: stacks to `1fr`, connector line hidden, step bg numbers hidden
- Reviews top: stacks to `1fr`
- Review cards: `1fr 1fr`
- Over Ons: stacks to `1fr`, rotated rect decorations hidden, image `aspect-ratio: 16/9`
- Contact: stacks to `1fr`
- Footer: `1fr 1fr` (2-column)

**≤768px (mobile)**
- Container `padding-inline: 20px`
- Review cards: `1fr`
- Footer: `1fr`
- Form row: `1fr` (was `1fr 1fr`)
- Mobile sticky CTA bar: shown (`display: flex`)
- Body: `padding-bottom: 72px` (to clear fixed bar)
- Nav links + phone: hidden

**≤480px**
- H1: forced to `36px`
- Section headings: `26px`
- Review score number: `64px`

### Container strategy

- Standard: `max-width: 1360px; margin-inline: auto; padding-inline: 40px`
- Full-bleed exceptions: wave divider (full viewport width), section backgrounds always extend edge-to-edge
- The inner content containers are consistent — section BGs are full-bleed, inner content is max-width constrained

### Sections that break the container

- Wave divider SVG: full viewport width
- Reviews + Footer section backgrounds: full viewport width with grain overlay
- Hero float card + badge: positioned to overlap image edges (extends past inner content column)

---

## 7. Decorative Elements

### 1. Ambient Blob Mesh (hero background)

```css
/* Two blurred gradient circles behind hero content */
.hero-blobs::before {
  position: absolute; top: -100px; left: -80px;
  width: 560px; height: 560px; border-radius: 50%;
  background: #0369A1; opacity: 0.055; filter: blur(90px);
}
.hero-blobs::after {
  position: absolute; top: 50%; left: 25%;
  width: 380px; height: 380px; border-radius: 50%;
  background: #FACC15; opacity: 0.07; filter: blur(70px);
}
```
**Placed**: Behind hero left content column. `pointer-events: none; overflow: hidden`.

### 2. Gentle Wave Divider (hero → USP transition)

```html
<div class="wave-divider" aria-hidden="true">
  <svg viewBox="0 0 1440 64" preserveAspectRatio="none" style="height:64px; display:block; width:100%;">
    <path d="M0,32 C240,64 480,0 720,32 C960,64 1200,0 1440,32 L1440,64 L0,64 Z" fill="#EFF6FF"/>
  </svg>
</div>
```
**Placed**: Between `<section class="hero">` and `<section class="usp-strip">`. Wave fill matches USP strip bg color (`#EFF6FF`). Parent bg is hero bg (`#FFFFFF`).

### 3. Gradient Underline on Highlighted Word

```css
.hl {
  position: relative; display: inline; color: #0369A1;
}
.hl::after {
  content: ''; position: absolute; bottom: 0; left: 0;
  width: 100%; height: 4px;
  background: linear-gradient(90deg, #0369A1, #0EA5E9);
  border-radius: 2px;
}
```
**Placed**: On `<span class="hl">` within H1 (hero) and H2 (over ons). Over Ons variant uses accent-to-light gradient: `linear-gradient(90deg, #FACC15, #0EA5E9)`.

### 4. Floating Stat Card + Accent Badge (hero image)

```css
/* Stat card — bottom-left of hero image */
.hero-float-card {
  position: absolute; bottom: -20px; left: -28px;
  background: #FFFFFF; border-radius: 20px;
  padding: 18px 22px; min-width: 160px;
  box-shadow: 0 8px 32px rgba(3,105,161,0.18);
  border: 1px solid #E5E7EB;
}
/* Accent badge — top-right of hero image */
.hero-float-badge {
  position: absolute; top: 20px; right: -20px;
  background: #FACC15; border-radius: 12px;
  padding: 10px 14px;
  box-shadow: 0 6px 20px rgba(234,179,8,0.35);
}
```
**Content**: Stat card shows "15+" + "jaar ervaring". Badge shows checkmark icon + "Morgen beginnen?".
**Responsive**: Hidden at ≤1024px.

### 5. V4 Scale Contrast — Oversized Step Numbers

```css
.step-bg-num {
  position: absolute; top: -12px; left: 50%;
  transform: translateX(-50%);
  font-family: Outfit; font-size: 128px; font-weight: 900;
  color: #0369A1; opacity: 0.04;
  pointer-events: none; user-select: none; z-index: 0;
}
```
**Placed**: Behind each timeline step card. Contains the step number ("1", "2", "3") as background texture.
**Responsive**: Hidden at ≤1024px (`.step-bg-num { display: none }`).

### 6. Grain/Noise Overlay (reviews + footer)

```css
/* SVG feTurbulence filter at 0.65 frequency, overlaid at 0.3 opacity (reviews) / 0.2 opacity (footer) */
/* Applied as SVG inside a position:absolute inset:0 element */
```
**Placed**: `<div class="reviews-grain">` and `.footer-grain` — absolute positioned, `pointer-events: none`.
Adds tactile texture to dark navy sections.

### 7. Rotated Rectangle Pair (over-ons image)

```css
.rect-bg-1 {
  position: absolute; top: -16px; right: -20px;
  width: 200px; height: 200px; border-radius: 28px;
  background: linear-gradient(135deg, rgba(3,105,161,0.12), rgba(14,165,233,0.06));
  transform: rotate(12deg);
}
.rect-bg-2 {
  position: absolute; bottom: -16px; left: -16px;
  width: 160px; height: 160px; border-radius: 20px;
  border: 2px solid rgba(3,105,161,0.15);
  transform: rotate(-6deg);
}
```
**Placed**: Behind the over-ons profile photo (`.over-ons-right`). `z-index: 0`, image at `z-index: 1`.
**Responsive**: Hidden at ≤1024px.

### 8. Decorative Circles in Reviews

```css
.reviews-circle {
  position: absolute; bottom: -120px; right: -120px;
  width: 400px; height: 400px; border-radius: 50%;
  background: #0369A1; opacity: 0.1;
}
.reviews-circle-2 {
  position: absolute; top: -80px; left: 30%;
  width: 300px; height: 300px; border-radius: 50%;
  background: #FACC15; opacity: 0.05;
}
```
**Placed**: Inside `.reviews` section, `pointer-events: none`.

### 9. Service Anchor Background Circle

```css
.service-anchor-bg-circle {
  position: absolute; top: -80px; right: -80px;
  width: 280px; height: 280px; border-radius: 50%;
  background: #0369A1; opacity: 0.18;
}
```
**Placed**: Inside dark anchor service card, `pointer-events: none`.

---

## 8. Design Suggestions

Layout suggestions selected in Prompt 3c, applied in homepage-reference.html:

| Code | Description | Applied |
|---|---|---|
| **L1** | Asymmetric hero (60/40 split) | Hero: `58fr 42fr` grid |
| **L2** | Asymmetric grid in services | Services: `5fr 3fr` with anchor spanning 2 rows |
| **L4** | Overlapping elements | Hero float card/badge overlap image boundary |
| **C3** | Process as timeline | Werkwijze: 3-step timeline with connector line |
| **V1** | Non-straight section divider | Wave SVG between hero and USP |
| **V3** | Dark background section | Reviews section (navy `#0F172A`) |
| **V4** | Scale contrast | Oversized step bg numbers (128px, 4% opacity) |

### Competitor patterns incorporated

| Pattern | Source | Applied in |
|---|---|---|
| Pill-shaped CTAs | CSU | All buttons use `border-radius: 9999px` |
| Cert badge repetition × 3 | Hensen | Hero trust strip → Over Ons floating bar → Certs section |
| Named testimonials with company | Hensen | Review cards: name + company + avatar initial |
| Editorial services grid with dark anchor | Hensen branches layout | Services: dark navy anchor card + 2 small white cards |
| CEO narrative + named director | Hensen | Over Ons: John van Ekeren profile card |
| Review score display (9.7/10) | Clean Up Tiel | Reviews: 80px score number with stars |
| Split hero layout | CSU | Hero 60/40 split with image right |

---

## 9. Animation Specification

### Animation level

**Level 5 — CSS-only.** No JS animation libraries. Budget: 0 KB extra.

### Approved effects

| Effect | Stars | Sections | Implementation |
|---|---|---|---|
| **Scroll fade-up** | ★★★★ | All content sections | CSS `@keyframes fadeUp` + `animation-delay` stagger |
| **Stagger reveal** | ★★★★ | Services grid, review cards, USP items | Sequential `animation-delay` on siblings |
| **Card lift hover** | ★★★★ | Service cards, contact methods | `transform: translateY(-4px)` + `box-shadow` transition |
| **Page-load cascade** | — | Nav, hero heading, hero sub, hero CTA | `opacity: 0` → `opacity: 1` with staggered delay |
| **Marquee** | ★★★★ | Optional: client logos / cert strip | CSS `@keyframes marquee` only if content warrants |

### Section-specific effects

| Section | Effect |
|---|---|
| Hero H1 | Page-load fade-in (delay 100ms) |
| Hero sub + CTA | Page-load cascade (delay 200ms, 300ms) |
| USP items | Stagger reveal on scroll (delay 0ms, 150ms, 300ms) |
| Service cards | Fade-up on scroll + card-lift on hover |
| Timeline steps | Stagger fade-up (delay 0ms, 200ms, 400ms) |
| Review cards | Stagger fade-up |
| Over Ons stats | Counter animation optional (CSS only) |

### CSS Implementation Reference (from effects library)

**Scroll fade-up** — CSS scroll-driven animation with IO fallback:
```css
/* Default: visible (zero CLS) */
.scroll-fade-up { opacity: 1; transform: translateY(0); }

@media (prefers-reduced-motion: no-preference) {
  @supports (animation-timeline: view()) {
    .scroll-fade-up {
      animation: fade-up linear both;
      animation-timeline: view();
      animation-range: entry 0% entry 100%;
    }
  }
  /* IO fallback for Firefox */
  .scroll-fade-up.js-scroll-reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.6s cubic-bezier(0.16, 1, 0.3, 1),
                transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
  }
  .scroll-fade-up.js-scroll-reveal.is-visible { opacity: 1; transform: translateY(0); }
}

@keyframes fade-up {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}
```

**Stagger reveal** — children appear one-by-one:
```css
@media (prefers-reduced-motion: no-preference) {
  @supports (animation-timeline: view()) {
    .stagger-container > * {
      animation: fade-up linear both;
      animation-timeline: view();
    }
    .stagger-container > *:nth-child(1) { animation-range: entry 0% entry 80%; }
    .stagger-container > *:nth-child(2) { animation-range: entry 5% entry 85%; }
    .stagger-container > *:nth-child(3) { animation-range: entry 10% entry 90%; }
  }
}
```

**Easing token**: `cubic-bezier(0.16, 1, 0.3, 1)` — the "reveal easing", used for all entrance animations.

### Reduced-motion fallback

**Required.** Wrap all scroll animations in:
```css
@media (prefers-reduced-motion: no-preference) {
  /* animation code here */
}
@media (prefers-reduced-motion: reduce) {
  .scroll-fade-up {
    opacity: 1 !important;
    transform: none !important;
    animation: none !important;
    transition: none !important;
  }
}
```
Default state must be visible (`opacity: 1`) — never set elements to `opacity: 0` outside the animation wrapper.

### Performance budget

- 0 KB JS (CSS-only path), ~0.5 KB for IntersectionObserver fallback (Firefox)
- All transitions ≤ 0.3s
- Only animate `opacity` + `transform` (compositor-only, no layout thrash)
- No `filter: blur()` animations (performance risk)
- Blob mesh uses static `filter: blur()` only (no animation)
- `animation-timeline: view()` browser support: ~83% (Chrome 115+, Edge 115+, Safari 26+)

---

## 10. CTA Architecture

### Primary contact method

**Offerte form** — 7 fields (4 required, 3 optional), always visible in contact section.

| Field | Name | Type | Placeholder | Required | Autocomplete |
|---|---|---|---|---|---|
| Voornaam | `voornaam` | text | "Jan" | yes | `given-name` |
| Achternaam | `achternaam` | text | "de Vries" | yes | `family-name` |
| Bedrijfsnaam | `bedrijf` | text | "Uw bedrijfsnaam" | yes | `organization` |
| E-mailadres | `email` | email | "jan@bedrijf.nl" | yes | `email` |
| Telefoonnummer | `telefoon` | tel | "06-12345678" | no | `tel` |
| Gewenste dienst | `dienst` | select | "Selecteer een dienst" | no | — |
| Toelichting | `bericht` | textarea | "Vertel kort over uw locatie, oppervlak en gewenste frequentie…" | no | — |

**Select options for "Gewenste dienst"**: Kantoorschoonmaak, Glazenwassen, Bouw-oplevering, Anders / combinatie

**Form layout**: Row 1 = voornaam + achternaam (2-col). Row 2 = bedrijfsnaam (full). Row 3 = email + telefoon (2-col). Row 4 = dienst (full). Row 5 = toelichting (full). At ≤768px all rows collapse to single column.

**Required field indicator**: Red asterisk `*` after label text (`<span style="color:red">*</span>`)

**Form button text**: `Offerte aanvragen` (primary button, full width, centered, with arrow icon)
**Never use**: "Versturen" or "Submit"

**AVG note below button**: `"Uw gegevens worden niet gedeeld met derden. AVG-conform."` (font-size 11px, centered, text-light color)

**Form heading**: "Offerte aanvragen" (form-heading style: Outfit 20px/700)
**Form subheading**: "Vul het formulier in — we reageren binnen 2 werkuren." (14px, text-muted)

### Secondary contact method

**Phone call**: `06 23545276` — shown as ghost outline button in hero and sticky mobile bar.

### CTA placement per section

| Section | CTA | Style |
|---|---|---|
| Nav (sticky) | "Offerte aanvragen" | `btn-primary btn-sm` |
| Hero | "Vrijblijvende offerte aanvragen" | `btn-primary` (icon arrow) |
| Hero | "Bel 06 23545276" | `btn-secondary` (icon phone) |
| Services header | "Alle diensten bekijken" | `btn-secondary` |
| Services anchor card | "Offerte aanvragen" | `btn-accent btn-sm` |
| Reviews section | "Offerte aanvragen" | `btn-accent` |
| Certs section | "Meer over kwaliteit" | `btn-primary btn-sm` |
| Contact form | "Offerte aanvragen" | `btn-primary form-submit` (full-width, icon arrow) |
| Mobile sticky bar | "Offerte aanvragen" + "Bellen" | `btn-primary` + `btn-secondary` (icon phone) |

### Sticky mobile CTA bar

- **Shown at**: ≤768px
- **Fixed**: `position: fixed; bottom: 0; left: 0; right: 0; z-index: 200`
- **Content**: Two equal-width buttons side by side
- **Body offset**: `padding-bottom: 72px` on body when bar is visible

---

## 11. Trust Signals

### Priority ranking (from Prompt 1 blueprint)

1. **Certificeringen** (VCA, Keurmerk Schoon) — top conversion driver for B2B
2. **Review score** (9.7/10 · 84 reviews) — third-party social proof
3. **Jaren ervaring** (Sinds 2009 / 15+ jaar) — longevity and reliability

### Placement per section

| Trust signal | Hero | Services | Reviews | Over Ons | Certs | Footer |
|---|---|---|---|---|---|---|
| VCA-gecertificeerd | ✓ eyebrow + strip | ✓ anchor features | — | — | ✓ badge | — |
| 9.7/10 · 84 reviews | ✓ strip | — | ✓ big display | — | — | — |
| Keurmerk Schoon | ✓ strip | — | — | ✓ floating bar | ✓ badge | ✓ badge |
| Sinds 2009 | ✓ strip | — | — | — | — | — |
| ISO 14001 | — | — | — | — | ✓ badge | — |
| SNA | — | — | — | — | ✓ badge | — |
| Schoonmakend NL | — | — | — | — | ✓ badge | — |
| Named testimonials | — | — | ✓ 3 cards | — | — | — |
| Owner profile (John) | — | — | — | ✓ profile card | — | — |

### Specific trust content

- **Review score**: 9.7/10 based on 84 beoordelingen
- **Stars**: ★★★★★ (5 stars)
- **Certifications**: VCA, Keurmerk Schoon, ISO 14001, SNA, Schoonmakend NL
- **Experience**: "Sinds 2009", "15+ jaar ervaring"
- **Owner**: John van Ekeren, Eigenaar
- **Guarantee text**: "Vaste medewerkers, transparante tarieven en persoonlijk aanspreekpunt"

---

## 12. Pricing Display

### Approach: **Hidden** (offerte-based)

This is a B2B kantoorschoonmaak business. No pricing is shown anywhere on the site. All CTAs drive toward the offerte form.

**Rationale**: Professional cleaning contracts are highly variable by square footage, frequency, and scope. Showing prices would disqualify leads prematurely or anchor expectations incorrectly.

### Copy approach

- Hero sub mentions "transparante tarieven" (builds trust without committing to numbers)
- USP strip: "Offerte binnen 24 uur na locatiebezoek. Transparante prijzen, geen verborgen kosten, eerlijk BTW-opgave."
- Form heading references gratis (free) quote

### If pricing is ever added in future

- Format: `EUR 49,-` or `vanaf EUR 49,-` (no comma for whole amounts)
- Thousands: period separator (`EUR 1.500,-`)
- Always include BTW note: `(excl. BTW)` or `(incl. BTW)`
- Never use `€` symbol alone — always spell `EUR`

---

## 13. Anti-Patterns (NEVER DO)

### Layout

- **NEVER** add `max-w-*` or `mx-auto` container wrappers not present in `homepage-reference.html`
- **NEVER** normalize padding/margin values across sections (they must vary intentionally)
- **NEVER** symmetrize asymmetric layouts from the reference (hero is 60/40, over-ons is 7/5 — keep these)
- **NEVER** make all service cards the same size — keep the large dark anchor + 2 small white cards
- **NEVER** center all content in a narrow wrapper

### Animation

- **NEVER** use `opacity: 0` as default state on GSAP-managed elements — set opacity:1, wrap reveal in `@media (prefers-reduced-motion: no-preference)`
- **NEVER** use only `fade-in-up` for all animations — vary the motion vocabulary
- **NEVER** animate `filter: blur()` (performance cost)

### Copy & UX

- **NEVER** use "Versturen" as form button text
- **NEVER** use "Submit" or untranslated English in UI
- **NEVER** mix je/jij with u/uw on the same site
- **NEVER** use aggressive sales language ("Wij zijn de #1 in…", "Beste schoonmaakbedrijf van Nederland")
- **NEVER** use countdown timers or fake urgency ("Nog 3 plekken beschikbaar!")
- **NEVER** use visible CAPTCHA — use honeypot instead
- **NEVER** use stock photography for team or project imagery

### Dutch conventions

- **NEVER** use comma as decimal if the number is whole (use `EUR 49,-` not `EUR 49,00`)
- **NEVER** write phone numbers without hyphens (`0623545276` → `06 23545276` or `06-23545276`)
- **NEVER** omit trailing slash on internal Astro links (`/diensten/` not `/diensten`)

---

## 14. Dutch UX Requirements

### Number & currency formatting

| Type | Format | Example |
|---|---|---|
| Currency (whole) | `EUR X,-` | `EUR 75,-` |
| Currency (decimal) | `EUR X,XX` | `EUR 74,95` |
| Large numbers | Period thousands | `EUR 1.500,-` |
| Percentages | Comma decimal | `99,7%` |

### Date & time formatting

| Type | Format | Example |
|---|---|---|
| Full date | Day + lowercase month + year | `15 maart 2026` |
| Month-year | Lowercase month | `maart 2026` |
| No ordinals | No "1e", "2de" for dates | `1 april`, not `1e april` |

### Contact formatting

| Type | Format | Example |
|---|---|---|
| Mobile phone | `06-XXXXXXXX` or `06 XX XX XX XX` | `06 23545276` |
| Local area | `0XXX-XXXXXX` | `0344-123456` |
| Postcode | `XXXX XX` (space between) | `4116 AB` |
| Email | Always lowercase | `info@johnsschoonmaakbedrijf.nl` |

### Legal requirements

- **KvK-nummer**: Required in footer (`KvK: XXXXXXXX`)
- **BTW-nummer**: Required in footer (`BTW: NLXXXXXXXXB01`)
- **Cookie banner**: Required, Dutch text, before analytics load
- **Privacy statement link**: Required in form AVG note and footer

### Hyphens for compound words

```html
<html lang="nl">  <!-- required on root -->
```
```css
body { hyphens: auto; } /* enable Dutch hyphenation */
```

### Trailing slashes

ALL internal links must end with `/`:
```html
<!-- Correct -->
<a href="/diensten/">Diensten</a>
<!-- Wrong -->
<a href="/diensten">Diensten</a>
```

Configured in `astro.config.mjs`: `trailingSlash: "always"`.

---

## 15. Design Reference

### Source hierarchy (highest to lowest authority)

1. **`DESIGN.md`** — token source of truth. When a value is specified here, use it exactly.
2. **`homepage-reference.html`** — visual reference for layout intent, spacing rhythm, and section feel. When DESIGN.md doesn't specify a detail, read the HTML.
3. **`competitor-reference/*.html`** — professional quality benchmark. Maintain visual parity or exceed.

### How to use during the Astro build

- When translating a section: read the corresponding CSS block in `homepage-reference.html`, then cross-reference token values in DESIGN.md.
- When a layout decision feels ambiguous: check the reference HTML first. If still unclear, check DESIGN.md section 6 (Grid & Layout).
- When adding a new component not in the reference: derive from the closest existing component tokens, matching the established visual language.
- When picking a color: use the CSS variable names from section 2, not raw hex (keeps theming consistent).

### Key files

| File | Purpose |
|---|---|
| `homepage-reference.html` | Complete single-page visual reference (open in browser) |
| `DESIGN.md` (this file) | Design token source of truth |
| `color-options.html` | Color exploration (reference only — Palette D chosen) |
| `typography-options.html` | Typography exploration (Optie 1 chosen: Outfit + Inter) |
| `layout-options.html` | Layout exploration (Optie 1 base + Optie 2 services + Optie 3 reviews) |
| `COMPETITORS.md` | Competitor analysis and design patterns |
| `competitor-reference/*.html` | Raw competitor HTML (layout inspiration) |
