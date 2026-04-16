# BUILD-PLAN.md — John's Schoonmaakbedrijf

> **Pre-build reference for Session 3.** Maps every homepage section to concrete layout patterns,
> effects, decorative elements, and component choices. All decisions filtered through:
> - Archetype E (Lifestyle/Personal Brand, schoonmaakbedrijf sub-type)
> - Animation level 5 (CSS-only, 0 KB JS budget)
> - DESIGN.md as token source of truth

---

## Layout Patterns

Three competitor patterns selected for reference during the Astro build. These complement
the patterns already incorporated (L1, L2, L4, C3, V1, V3, V4 — see DESIGN.md section 8).

### 1. Hensen — Editorial Services Grid with Dark Anchor

- **Source:** `competitor-reference/hensen-cleaning.html`, solutions/branches section
- **Grid:** Bootstrap `col-lg-4` (3 equal columns), `row g-4` (1rem gap), with one card visually dominant via dark background and larger padding
- **Why it fits:** Already adapted in DESIGN.md as the `5fr 3fr` asymmetric services grid with dark anchor card spanning 2 rows. During the build, reference Hensen's card proportions and how they balance the dominant card against smaller cards. The dark anchor pattern communicates "flagship service" — critical for B2B kantoorschoonmaak positioning.

### 2. CSU — Asymmetric Sidebar + Content Area (25/75)

- **Source:** `competitor-reference/csu.html`, news-slider section (line ~628)
- **Grid:** `col col--xl-1/4` (25% sidebar, dark bg) + remaining 75% for content/carousel
- **Why it fits:** Validates the asymmetric split approach used in our Reviews section (`3fr 5fr` = ~37/63 split). During the build, reference CSU's dark sidebar treatment for how dark backgrounds anchor content blocks. The 25/75 ratio also informs potential future "aside" layouts on subpages.

### 3. EW-Facility — Full-Width CTA Banner with Background Figure

- **Source:** `competitor-reference/ew-facility.html`, `section--banner` and `section--topics`
- **Grid:** Full-viewport-width dark section with centered `col-sm-6 col-sm-push-3` (50% width, centered)
- **Why it fits:** Informs how the Certs strip and mobile CTA bar should handle full-bleed backgrounds with constrained inner content. The `col-sm-push-3` centering trick (offset by 25%) creates visual breathing room without explicit `max-width` containers — a pattern we can replicate with CSS Grid `justify-self: center`.

---

## Effects Selection

**Archetype E intensity ratings** from `reference-effects-library.md` section 6.
Filtered to **3+ only**, then cross-checked against the **0 KB JS budget** (animation level 5).

### CSS-Only Effects (approved — 0 KB JS)

| Effect | E Score | Sections | Implementation | Notes |
|---|---|---|---|---|
| **Scroll fade-up** | 4 | All content sections | CSS `@keyframes fadeUp` + `animation-timeline: view()` | IO fallback for Firefox (~0.5 KB) |
| **Stagger reveal** | 4 | Services grid, review cards, USP items, timeline | Sequential `animation-delay` on siblings | Stagger 150ms between children |
| **Scale reveal** | 3 | Hero image, Over Ons image | CSS `@keyframes scaleIn` + scroll-driven | `transform: scale(0.95)` → `scale(1)` |
| **Card lift hover** | 4 | Service cards, contact methods, review cards | `transform: translateY(-4px)` + `box-shadow` transition | Already in DESIGN.md component styles |
| **Image overlay** | 4 | Service anchor card, hero image area | CSS gradient overlay on `::after` pseudo | Static, no animation needed |
| **Floating elements** | 3 | Hero stat card, hero badge | CSS `@keyframes float` (gentle 3px bob) | `animation: float 6s ease-in-out infinite` |
| **Gradient mesh** | 4 | Hero background | Static `filter: blur()` on positioned circles | Already in DESIGN.md section 7.1 |
| **Pulsing CTA** | 3 | Mobile sticky bar "Bellen" button | CSS `@keyframes pulse` ring animation | Subtle — `box-shadow` pulse only |
| **Marquee** | 4 | Optional: certs strip or client logos | CSS `@keyframes marquee` horizontal scroll | Only if content warrants continuous scroll |
| **View transitions** | 4 | Page navigation (multi-page) | Astro `<ViewTransitions />` built-in | 0 KB — browser native API |
| **Skeleton shimmer** | 3 | Image placeholders during lazy-load | CSS `@keyframes shimmer` gradient | Optional, only for slow-loading images |

### Excluded (rated 3+ for E, but requires GSAP)

| Effect | E Score | Reason excluded |
|---|---|---|
| Background parallax | 4 | Requires GSAP ScrollTrigger or complex CSS `perspective` hack |
| Offset parallax | 3 | Requires GSAP ScrollTrigger |
| Image zoom on scroll | 3 | Scroll-driven zoom needs JS for smooth control |
| SplitText | 3 | Requires GSAP SplitText plugin (~4.5 KB) |
| Clip-path reveals | 3 | Complex scroll-driven clip needs GSAP |
| Color transitions | 3 | Scroll-triggered color changes need JS state |

### Section-Specific Effect Map

| Section | Effects Applied |
|---|---|
| **Nav** | — (static, no animation) |
| **Hero** | Page-load cascade (heading → sub → CTA), gradient mesh bg, floating bob on stat card/badge |
| **USP Strip** | Stagger reveal on scroll (0ms, 150ms, 300ms) |
| **Services** | Fade-up on scroll, card lift hover, image overlay on anchor card |
| **Werkwijze** | Stagger fade-up (0ms, 200ms, 400ms), scale reveal on step icons |
| **Reviews** | Stagger fade-up on cards, scale reveal on score number |
| **Over Ons** | Fade-up on text, scale reveal on profile image |
| **Certs** | Fade-up (single group), optional marquee if many badges |
| **Contact** | Fade-up on form and info block |
| **Footer** | — (static, no scroll animation) |
| **Mobile CTA** | Pulsing ring on phone button |

---

## Visual Craft Elements

DESIGN.md section 7 already defines 9 decorative elements. These 5 additions are from
`reference-visual-craft-library.md`, all rated **\*\*** or **\*\*\*** for Archetype E.

### 1. Giant Quote Marks — Reviews Section

- **Element:** Giant decorative `"` marks behind review blockquotes
- **Craft library rating:** ★★★ for E
- **Section:** Reviews (dark navy background)
- **Implementation:** CSS `::before` pseudo-element with oversized font
- **Color:** `rgba(255, 255, 255, 0.04)` — barely visible on `#0F172A` navy
- **Code:**
  ```css
  .review-card::before {
    content: '\201C'; /* left double quotation mark */
    position: absolute; top: -8px; left: 16px;
    font-family: Georgia, serif; font-size: 96px;
    color: rgba(255, 255, 255, 0.04);
    pointer-events: none; line-height: 1;
  }
  ```

### 2. Icon with Gradient Background — USP Strip & Service Cards

- **Element:** Icon wrappers with gradient fill instead of flat color
- **Craft library rating:** ★★★ for E
- **Section:** USP strip icons, service card icons
- **Implementation:** `background: linear-gradient()` on icon wrapper divs
- **Colors mapped to palette:**
  - Primary gradient: `linear-gradient(135deg, #0369A1, #0EA5E9)` (primary → primary-light)
  - Icon color: `#FFFFFF` on gradient bg
- **Replaces:** Flat `#E0F2FE` background from DESIGN.md (upgrade, not replacement — use gradient for USP strip, keep flat for service cards to maintain variety)

### 3. Asymmetric Image Corners — Over Ons Profile Photo

- **Element:** Non-uniform `border-radius` on the profile image
- **Craft library rating:** ★★★ for E
- **Section:** Over Ons (profile photo of John van Ekeren)
- **Implementation:** `border-radius` shorthand with 4 different values
- **Color:** N/A (shape treatment, not color)
- **Code:**
  ```css
  .over-ons-image {
    border-radius: 28px 12px 28px 12px; /* TL TR BR BL */
    /* Creates organic, non-mechanical shape */
  }
  ```
- **Pairs with:** Rotated rectangle pair (DESIGN.md section 7.7) behind the image

### 4. Circle-Arrow CTA — Secondary Buttons

- **Element:** Small circle with arrow icon appended to secondary CTAs
- **Craft library rating:** ★★ for E
- **Sections:** "Alle diensten bekijken" (services), "Meer over kwaliteit" (certs)
- **Implementation:** `::after` pseudo-element with circular border and arrow SVG
- **Colors mapped to palette:**
  - Circle border: `#0369A1` (primary)
  - Arrow: `#0369A1`
  - Hover: circle fills `#0369A1`, arrow turns `#FFFFFF`
- **Code:**
  ```css
  .btn-arrow::after {
    content: ''; display: inline-flex; align-items: center; justify-content: center;
    width: 28px; height: 28px; margin-left: 10px;
    border: 2px solid #0369A1; border-radius: 50%;
    background: url("data:image/svg+xml,...") center/14px no-repeat;
    transition: all 0.2s;
  }
  .btn-arrow:hover::after {
    background-color: #0369A1;
    /* arrow SVG switches to white */
  }
  ```

### 5. S-Curve Flourish — Hero Eyebrow Area

- **Element:** Subtle decorative S-curve line near the hero kicker/eyebrow pill
- **Craft library rating:** ★★★ for E
- **Section:** Hero, positioned beside or below the eyebrow pill
- **Implementation:** Inline SVG, static (no animation)
- **Colors mapped to palette:**
  - Stroke: `#0EA5E9` (primary-light) at 20% opacity
  - Stroke-width: 2px
- **Note:** Keep small (max 120px wide) — decorative accent, not a focal point. Hidden at ≤768px.

---

## Component Choices

Decision priority: **framework-agnostic first** (Preline, Flowbite, DaisyUI — 0 JS overhead) →
React-based only if interactivity requires it → 21st.dev for inspiration.

### Per-Section Component Map

| Section | Component | Source | `client:load`? | Rationale |
|---|---|---|---|---|
| **Nav** | Preline Navbar | Preline UI | No | Static links + CSS-only mobile toggle (checkbox hack). No JS overhead. |
| **Hero** | Custom Astro | — | No | 60/40 split with float card/badge is too specific for any library. Reference 21st.dev "hero split" for structure inspiration. |
| **USP Strip** | Custom Astro | — | No | 3-col flex with border separators. Too simple to warrant a library component. |
| **Services** | Preline Cards (adapted) | Preline UI | No | Use Preline card markup for white service cards. Dark anchor card is fully custom (no library match for asymmetric span-2 dark card). |
| **Werkwijze** | Preline Timeline | Preline UI | No | 3-step horizontal timeline. Preline has timeline components with step indicators. Adapt to match connector line overlay from DESIGN.md. |
| **Reviews** | Custom Astro | — | No | Dark-bg glassmorphism cards + 80px score display. No library has this specific dark card style. Reference 21st.dev "testimonial cards" for content structure. |
| **Over Ons** | Custom Astro | — | No | 7/5 split with profile card and decorative elements. Too specific for libraries. |
| **Certs** | Flowbite Badge Row | Flowbite | No | Flex row of badge components. Flowbite has badge + icon patterns. Adapt colors to palette. |
| **Contact** | Preline Form + Custom | Preline UI | No | Preline form field components (input, select, textarea) for consistent styling. Layout grid is custom. HTML5 native validation, no JS. |
| **Footer** | Preline Footer | Preline UI | No | 4-column footer template. Adapt to dark navy bg + badge styles from DESIGN.md. |
| **Mobile CTA** | Custom Astro | — | No | Fixed bottom bar with 2 buttons. Pure CSS positioning. ~10 lines of markup. |
| **Cookie Banner** | Custom Astro | — | Minimal | Requires tiny vanilla JS for dismiss + localStorage. Not a React island. |

### Interactivity Assessment

| Interactive Element | Approach | JS Cost |
|---|---|---|
| Mobile nav toggle | CSS checkbox hack (`input:checked ~ .nav-menu`) | 0 KB |
| FAQ accordion (if added) | HTML `<details>/<summary>` | 0 KB |
| Form validation | HTML5 `required`, `type="email"`, `type="tel"` | 0 KB |
| Form submission | Astro server endpoint or Cloudflare Pages Function | 0 KB client-side |
| Cookie consent | Vanilla JS (~0.3 KB inline) | 0.3 KB |
| IO scroll fallback | Vanilla JS IntersectionObserver (~0.5 KB) | 0.5 KB |
| **Total client JS** | | **~0.8 KB** |

### Component Fetch Commands (for build phase)

```bash
# Preline (no MCP — copy from preline.co)
npm install preline
# Then browse preline.co for: navbar, cards, timeline, form, footer

# Flowbite (via MCP)
npx -y flowbite-mcp
# Then: search for badge components

# 21st.dev (via MCP, inspiration only)
# magic MCP → 21st_magic_component_inspiration
#   searchQuery: "hero split"
#   searchQuery: "testimonial cards"
#   searchQuery: "contact form"
```

---

## Anti-Patterns

### From DESIGN.md Section 13

**Layout:**
- NEVER add `max-w-*` or `mx-auto` container wrappers not present in `homepage-reference.html`
- NEVER normalize padding/margin values across sections (they must vary intentionally)
- NEVER symmetrize asymmetric layouts from the reference (hero is 60/40, over-ons is 7/5 — keep these)
- NEVER make all service cards the same size — keep the large dark anchor + 2 small white cards
- NEVER center all content in a narrow wrapper

**Animation:**
- NEVER use `opacity: 0` as default state on GSAP-managed elements — set opacity:1, wrap reveal in `@media (prefers-reduced-motion: no-preference)`
- NEVER use only `fade-in-up` for all animations — vary the motion vocabulary
- NEVER animate `filter: blur()` (performance cost)

**Copy & UX:**
- NEVER use "Versturen" as form button text
- NEVER use "Submit" or untranslated English in UI
- NEVER mix je/jij with u/uw on the same site
- NEVER use aggressive sales language ("Wij zijn de #1 in...", "Beste schoonmaakbedrijf van Nederland")
- NEVER use countdown timers or fake urgency ("Nog 3 plekken beschikbaar!")
- NEVER use visible CAPTCHA — use honeypot instead
- NEVER use stock photography for team or project imagery

**Dutch conventions:**
- NEVER use comma as decimal if the number is whole (use `EUR 49,-` not `EUR 49,00`)
- NEVER write phone numbers without hyphens (`0623545276` -> `06 23545276` or `06-23545276`)
- NEVER omit trailing slash on internal Astro links (`/diensten/` not `/diensten`)

### Additional Build-Phase Anti-Patterns

**Performance:**
- NEVER set `opacity: 0` on hero elements (H1, hero image, hero CTA) — this is the **LCP trap**. Chrome skips invisible elements for LCP calculation, pushing LCP from <2s to 5.3s. Use `opacity: 1` as default, animate with `transform` only, or use `opacity: 0.1` minimum.

**Visual monotony:**
- NEVER apply uniform `py-*` on 3+ consecutive sections — DESIGN.md section 4 specifies intentionally varied padding (hero `pt:80 pb:64`, USP `py:48`, services `pt:80 pb:96`, werkwijze `pt:80 pb:112`, etc.). Uniform padding kills visual rhythm.
- NEVER use a centered-everything layout — the design intentionally uses left-aligned hero text, asymmetric grids (60/40, 7/5, 5/3), and varied text alignment per section. Centering everything signals "generic template".
- NEVER reuse identical card components across sections — service cards, review cards, step cards, and contact method cards each have distinct padding, radius, shadow, and background values (see DESIGN.md section 5). Same component with different content is not enough differentiation.
