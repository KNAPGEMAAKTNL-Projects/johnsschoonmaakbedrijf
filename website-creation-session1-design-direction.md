# Session 1 — Design Direction

> Single session. ~60 minutes. Output: `DESIGN.md` + `homepage-reference.html`
> Skills: `frontend-design` (activate for Prompts 3c, 4)
> MCPs: `coolors`, `google-fonts`, `playwright`

## Prerequisites

- Client info collected (business name, URL, niche, location, services, brand assets)
- Project folder created (empty directory, Claude Code opened inside it)

---

## Prompts

### Prompt 0 — Project Setup

```
Set up this project folder for a new website build. Do the following:

1. Run `git init` to initialize a git repository.

2. Copy the project template from the Hub:
   cp -r "C:/Users/yanni/Hub/business/templates/claude-project-template" ".claude"
   This gives us the full setup including agents, helpers, hooks, settings, rules
   (astro-conversion.md, design-fidelity.md), and skills.

3. Create `.mcp.json` with this exact content:
{
  "mcpServers": {
    "claude-flow": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "@claude-flow/cli@latest", "mcp", "start"],
      "env": {
        "npm_config_update_notifier": "false",
        "CLAUDE_FLOW_MODE": "v3",
        "CLAUDE_FLOW_HOOKS_ENABLED": "true",
        "CLAUDE_FLOW_TOPOLOGY": "hierarchical-mesh",
        "CLAUDE_FLOW_MAX_AGENTS": "15",
        "CLAUDE_FLOW_MEMORY_BACKEND": "hybrid"
      },
      "autoStart": true
    }
  }
}

4. Create `CLAUDE.md` with this content:

# [John's Schoonmaakbedrijf] Project Guidelines

## Brand Name
Always write the brand name as **[John's Schoonmaakbedrijf]** (exact format).

## Tech Stack
- Framework: Astro 5 (Static Site Generation)
- Styling: Tailwind CSS 4 (via @tailwindcss/vite, NOT @astrojs/tailwind)
- Deployment: Cloudflare Pages
- Animation: CSS-only (or GSAP if DESIGN.md specifies animation level 7+)

## Design System
Read `DESIGN.md` before making ANY visual decisions. It is the single source of truth.
Read `.claude/rules/astro-conversion.md` and `.claude/rules/design-fidelity.md` — these MUST be followed during builds.

## Design Reference
`homepage-reference.html` is the visual reference. `DESIGN.md` is the token source of truth.
During builds, reference both — homepage-reference.html for layout intent, DESIGN.md for exact values.

## Skills
Activate `frontend-design` for any HTML generation tasks (design previews, homepage reference, component prototyping).

## Critical Rules
- All internal links MUST end with trailing slash (Astro trailingSlash: "always")
- All text in Dutch unless specified otherwise
- Use je/jij (check DESIGN.md for exceptions)
- All formatting: Dutch conventions (comma decimals, period thousands, EUR before amount with space)
- Date format: "15 maart 2026" (day first, lowercase month)
- Phone format: 06-12345678 or local area code
- Postcode format: 1234 AB
- Never use stock photos for team/project imagery
- Never use "Versturen" as form button text
- Never use aggressive sales language ("Wij zijn de #1...")
- NEVER add max-w-*, mx-auto, or container wrappers not in the reference HTML
- NEVER normalize padding/margin values across sections
- NEVER symmetrize asymmetric layouts from the reference design

5. Create `.gitignore` with:
node_modules/
dist/
.astro/
.env
.env.*
.DS_Store

6. Stage all files and create an initial commit with message "chore: initial project setup"
```

**Replace `[Client Name]` and `[CLIENT BRAND NAME]` with the actual client details before running.**

---

### Prompt 1 — Business Discovery & Archetype

```
Read the business-type blueprints reference at C:\Users\yanni\Hub\business\sops\reference-business-type-blueprints.md.
Read the effects library at C:\Users\yanni\Hub\business\sops\reference-effects-library.md (just the intensity mapping table).
Read the conversion patterns at C:\Users\yanni\Hub\business\sops\reference-conversion-patterns.md (CTA architecture section).

We are starting a new website project. Here is the client information:

- Business Name: [John's Schoonmaakbedrijf]
- Current Website URL: [https://johnsschoonmaakbedrijf.nl/]
- Niche/Industry: [Schoonmaakbedrijf]
- Location (City, Region): [Buren]
- Service Area: [Check website for location pages, quite a lot]
- Primary Service/Product: [johnsglazenwassersbedrijf is the business, but he's moving his business towards kantoorschoonmaak etc for businesses. He does all the services he does now, except dakpannen reinigen. ]
- Brand assets available: @logo(1).png added to root.
- Photos available: there are pictures from the current website thta we can use. 
- Client's personality/vibe: [approachable]

Based on this information and the blueprints reference:

1. Identify the business archetype (A through E) and look up the FULL blueprint.

2. Show me:
   - Archetype + visual tone scores (energy, density, formality, richness, animation)
   - Proposed homepage section order
   - Hero type recommendation
   - Trust signal priority ranking (top 3)
   - CTA architecture (primary + secondary contact method, form fields, button text — cross-reference with conversion patterns)
   - Pricing display approach (full/range/hidden)
   - Animation level and what effects are appropriate (from intensity mapping)
   - Common mistakes to avoid for this business type

3. If the client has an existing website, read it and note what works and what doesn't.

4. Note: "Client HAS brand colors/fonts: [yes/no]" — this determines color/typography approach in Prompts 3a-3b.

5. SUB-VARIANT CHECK: Some business types need a B2B/B2C split. Ask me:

   For Schoonmaakbedrijven: "Is this primarily B2B (kantoren, bedrijven), B2C (particulieren, woningen), or mixed?"
   - B2B: bump formality to 6, CTA = "Offerte aanvragen", trust = client logos + case studies, typography = structured (Inter, Roboto)
   - B2C: keep formality at 3, CTA = "Bereken prijs" or "Bestel nu", trust = reviews + price transparency, typography = rounded friendly (Nunito, Quicksand)
   - Mixed: default to primary audience for hero, add secondary pathway as separate section

   For Schilders: "Is this primarily residential or commercial?"
   - Residential: warmer tone, before/after photos of homes, "je/jij", pricing per m2
   - Commercial: slightly more formal, project photos of offices/buildings, "u" optional, offerte-based

   For Bouwbedrijven/Aannemers: "Is this renovatie (consumers) or nieuwbouw (developers)?"
   - Renovatie: B2C approach, portfolio of home renovations, "je", price ranges
   - Nieuwbouw: B2B approach, project references, "u", offerte only

   For Installateurs: "Is this primarily consumers (cv-ketel) or businesses (klimaatsystemen)?"
   - Consumer: emergency CTA prominent, pricing visible, "je"
   - Business: offerte-focused, certifications prominent, "u" acceptable

   If none of these apply, skip this step.

Show me everything including the sub-variant answer. I will confirm or adjust before we continue.
```

---

### Prompt 2a — Competitor Research

```
Research 10 competitors for this business.

Research mix:
- 5 local competitors: search "[service] [city]" and "[service] [region]"
- 5 national leaders: search "beste [service] Nederland" or "[service] [major city]"

Create `COMPETITORS.md` in the project root with this table:

| # | Site | URL | What stands out | Hero approach | Trust signals used | CTA approach | My rating |
|---|------|-----|-----------------|---------------|-------------------|-------------|-----------|
| 1 | | | | | | | /10 |
| ... | | | | | | | /10 |

Leave "My rating" empty — I will fill it in.

After the table, answer:
1. What is the "local baseline"?
2. What do the national leaders do differently?
3. What mistakes do the worst competitors make?

Save as COMPETITORS.md.
```

-> HUMAN: Open each competitor URL. Rate them 1-10 on design quality in COMPETITORS.md. Then continue with Prompt 2b.

---

### Prompt 2b — Analyze Top-Rated Competitors

```
Read COMPETITORS.md. Look at my ratings.

For the top 3 highest-rated competitors:
- Use WebFetch to fetch each site's full HTML
- Save the raw HTML to: competitor-reference/[site-name].html
- Analyze: section order, typography, colors, spacing, trust signals, CTA, animation, decorative elements
- SPECIFICALLY look for: full-bleed sections, asymmetric grids, overlapping elements, decorative SVG shapes, varying section padding

For the lowest-rated:
- What makes them look bad?

Summarize:
1. Top 3-5 design decisions to incorporate
2. CSS layout patterns that make the best ones look professional

Save analysis to COMPETITORS.md. HTML files in competitor-reference/ will be referenced during design generation.
```

---

### Prompt 3a — Color Options

```
Read the following before starting:
- Prompt 1 output (archetype, tone scores, brand asset status)
- COMPETITORS.md (top-rated competitors and their color approaches)
- competitor-reference/*.html (actual HTML from top competitors — extract color values)
- C:\Users\yanni\Hub\business\sops\reference-business-type-blueprints.md (archetype color psychology)

If the client has a logo file, use coolors MCP `extract_image_colors` to pull the dominant colors from it.

For each top-rated competitor in competitor-reference/*.html, extract their color palette (primary, secondary, accent, background, text colors).

Now generate a file called `color-options.html` with 3 palette options. Each palette must define: primary, secondary, accent, background, surface, and text colors.

OPTION A — Brand-Anchored:
- If client HAS brand colors: use those exactly as primary/secondary. Derive accent, background, surface, text to complement them. Use coolors MCP `harmonize_colors` to find complementary tones.
- If client has NO brand colors: derive from archetype color psychology in the blueprints. Use specific hex values that match the archetype mood (e.g., deep forest green for hoveniers, clinical blue for tandartsen). Use coolors MCP `generate_palette` seeded from the archetype's mood color.

OPTION B — Competitor-Inspired:
- Take the highest-rated competitor's palette as a starting point. Do NOT copy it — shift hues by 15-30 degrees, adjust saturation/lightness to create a distinct but equally professional palette. Use coolors MCP `harmonize_colors` on the shifted base.

OPTION C — Creative Contrast:
- Design a palette that stands out from ALL competitors in the market. Use archetype mood as the emotional anchor but pick unexpected color angles. If all competitors use blue, go warm. If all use neutrals, introduce a bold accent. Use coolors MCP `generate_palette` with the contrast concept.

For each palette option, use coolors MCP `check_contrast` to verify:
- Text on background: WCAG AA minimum (4.5:1)
- Large text on background: WCAG AA (3:1)
- Button text on button background: WCAG AA (4.5:1)

The HTML file must:
- Show each palette as visual swatches (large colored rectangles with hex values labeled below each)
- Show a mini section preview for each palette: a hero-like block with heading (in the heading color on the background), subtext (in the text color), and a CTA button (in the accent/primary on a contrasting background)
- Use actual hex values labeled clearly next to every swatch
- Be self-contained: inline CSS, no external dependencies except Google Fonts CDN if needed for preview text
- Include a title "Kleurpaletten — [Client Name]" at the top
- Show color role labels: Primair, Secundair, Accent, Achtergrond, Oppervlak, Tekst

Save as `color-options.html` in the project root.
```

-> HUMAN: Open `color-options.html` in browser. Pick favorite palette (or say "mix A primary with C accent" etc).

---

### Prompt 3b — Typography Options

```
Read the following before starting:
- Prompt 1 output (archetype, tone scores, formality level)
- COMPETITORS.md (what fonts the top competitors use)
- C:\Users\yanni\Hub\business\sops\reference-business-type-blueprints.md (archetype typography personality)

If the client has a brand font, that font is locked for headings. Use google-fonts MCP `list_pairings` to find 3 body font pairings for it.

If the client has NO brand font, use google-fonts MCP to find 3 complete heading + body pairings:
- Use `search_fonts` with the archetype personality keywords (e.g., "geometric modern" for archetype A, "organic rounded" for archetype B hoveniers, "clean clinical" for archetype D)
- Use `list_pairings` for each candidate heading font to get recommended body pairings
- Each pairing should have a different character: one classic/safe, one modern/distinctive, one expressive/bold

Generate a file called `typography-options.html` with 3 font pairing options.

For each option show:
- Font names and weights clearly labeled (e.g., "Space Grotesk 700 + Inter 400/600")
- Google Fonts category (sans-serif, serif, display)
- A hero headline in Dutch: 5-7 words, realistic for the business type (e.g., "Uw tuin, ons meesterwerk" or "24/7 loodgieterservice in Utrecht")
- A subtext line: 15-25 words in Dutch, realistic service description
- A body paragraph: 3-4 sentences of realistic Dutch service business text (NOT lorem ipsum)
- A CTA button: "Vraag gratis offerte aan"
- Nav links row: Home | Diensten | Over ons | Portfolio | Contact
- A Dutch compound word stress test: show "schoonmaakdiensten", "tuinonderhoud", "verwarmingsinstallatie", "kantoorschoonmaak" at heading size to check if the font handles long Dutch words without awkward breaks

For each option, show at TWO widths side by side (or stacked):
- Desktop: 1440px max-width preview
- Mobile: 375px max-width preview

Include character budget info per option:
- Characters per line at H1 size (desktop)
- Characters per line at body size (desktop)
- Whether the font has Dutch-specific glyphs (ij ligature, accented vowels)

Load all fonts via Google Fonts CDN `<link>` tags.
The HTML must be self-contained: inline CSS, no external dependencies beyond Google Fonts CDN.
Include a title "Typografie — [Client Name]" at the top.

Save as `typography-options.html` in the project root.
```

-> HUMAN: Open `typography-options.html` in browser. Pick favorite pairing.

---

### Prompt 3c — Layout, Hero & Effects

**Skill: activate `frontend-design`**

```
Read the following before starting:
- Prompt 1 output (archetype, tone scores, section order, hero recommendation)
- COMPETITORS.md (top-rated design patterns, layout analysis)
- competitor-reference/*.html (actual HTML from top competitors)
- C:\Users\yanni\Hub\business\sops\reference-business-type-blueprints.md (archetype constraints)
- C:\Users\yanni\Hub\business\sops\reference-effects-library.md (intensity mapping for this archetype)
- C:\Users\yanni\Hub\business\sops\reference-visual-craft-library.md (decorative elements selection guide)
- The chosen color palette from Prompt 3a (whichever option the human picked)
- The chosen typography from Prompt 3b (whichever pairing the human picked)

PART A — LAYOUT SUGGESTIONS:
Pick 3-5 layout suggestions from this menu based on archetype + what the top competitors do well:

LAYOUT:
- L1: Asymmetric hero (60/40 or 70/30 split)
- L2: Asymmetric grid in services/content section (not equal columns)
- L3: Full-bleed section (edge-to-edge, breaking the container)
- L4: Overlapping elements (image overlapping section boundary)

CONTENT PRESENTATION:
- C1: Services as editorial layout instead of card grid
- C2: Horizontal scroll element (for portfolio, logos, or testimonials)
- C3: Process/werkwijze as timeline instead of numbered steps
- C4: FAQ accordion (always recommended — AI SEO critical)

VISUAL ELEMENTS:
- V1: Non-straight section divider (wave, diagonal, curved)
- V2: Background texture or pattern in one section
- V3: Dark background section for contrast
- V4: Scale contrast (oversized numbers + small labels)

Also check: what did the top-rated competitors from Prompt 2b do that we liked? Add those patterns as suggestions too.

PART B — HERO TYPE:
Recommend a hero type based on archetype + what competitors do:
- Split (60/40), Full-Bleed Image, Typography Hero, CTA-First, Booking Hero, Before/After

PART C — EFFECTS:
From the effects library intensity mapping, list effects appropriate for this animation level.
Categorize as: scroll-triggered, hover, page-load, continuous.
Note the performance budget from the effects library.

PART D — GENERATE LAYOUT OPTIONS HTML:
Using the `frontend-design` skill, generate `layout-options.html` showing 2-3 hero/layout approaches.

Each option must:
- Apply the chosen color palette and typography from Prompts 3a-3b
- Show a full hero section (with heading, subtext, CTA button, image placeholder area)
- Show one content section below the hero (services, stats, or werkwijze — whichever best demonstrates the layout approach)
- Use the layout suggestions from Part A applied differently in each option
- Draw inspiration from competitor-reference HTML patterns (professional spacing, grid structures)
- Reference specific visual craft library elements by name (e.g., "Gentle Wave divider between hero and services", "Blur Blob behind hero image")

The HTML must be self-contained: inline CSS + Google Fonts CDN only.
Include a title "Layout Opties — [Client Name]" at the top.
Label each option clearly: "Optie 1: [description]", "Optie 2: [description]", etc.

Save as `layout-options.html` in the project root.

Show me: layout suggestions + hero recommendation + effects list + the generated HTML file.
```

-> HUMAN: Open `layout-options.html` in browser. Pick favorite layout approach. Confirm or adjust the effects list.

---

### Prompt 4 — Full Homepage Reference

**Skill: activate `frontend-design`**

```
Read the following before starting:
- Prompt 1 output (archetype, full blueprint: section order, hero, CTA, trust signals, pricing display)
- COMPETITORS.md (design patterns analysis)
- competitor-reference/*.html (actual HTML — use for layout inspiration, NOT to copy)
- C:\Users\yanni\Hub\business\sops\reference-visual-craft-library.md (FULL file — decorative elements with code)
- C:\Users\yanni\Hub\business\sops\reference-effects-library.md (FULL file — for effect descriptions, NOT for implementation code yet)
- The chosen color palette from Prompt 3a
- The chosen typography from Prompt 3b
- The chosen layout approach from Prompt 3c (hero type, layout suggestions, effects list)

Using the `frontend-design` skill, generate a complete single-page HTML homepage.

SECTIONS — follow the archetype blueprint section order from Prompt 1. For EACH section, include:
- Real placeholder Dutch text (realistic for this business type — NOT lorem ipsum)
- The appropriate layout pattern from the chosen approach
- Visual craft elements from reference-visual-craft-library.md (reference them by name)
- Colors and typography exactly as chosen in Prompts 3a-3b

DESIGN CRAFT RULES — follow ALL of these:

1. SECTION PADDING MUST VARY: hero pt-32 pb-20, stats py-12, services py-24, process pt-20 pb-28, reviews py-24, about pt-16 pb-24, contact py-24, footer pt-16 pb-8. Do NOT use uniform padding.

2. SECTION BACKGROUNDS MUST VARY: alternate between light (background color), white (surface color), dark (primary-900 or similar), accent-tinted (primary at 5% opacity), image backgrounds. At least one dark section. At least one accent-tinted section.

3. LAYOUT MUST NOT BE UNIFORM:
   - Do NOT center everything in a narrow container
   - Do NOT make all cards the same size
   - Do NOT use only rectangles with no decorative shapes
   - DO use asymmetric grids where the archetype calls for it (7/5, 8/4, 3/3/6)
   - DO let at least one element break the container edge (full-bleed or offset)
   - DO vary card sizes within a grid (e.g., one large + two small, or editorial mixed layout)

4. DECORATIVE ELEMENTS — pick 3-5 from the visual craft library and apply them:
   - Name each one in an HTML comment where it's used (e.g., <!-- Visual Craft: Gentle Wave Divider -->)
   - Replace color values with the chosen palette colors
   - Place them at section transitions, behind hero images, or as accent details

5. TYPOGRAPHY HIERARCHY — use the chosen fonts with clear hierarchy:
   - H1: hero only, largest size (48-72px depending on archetype energy)
   - H2: section headings, clearly smaller than H1
   - H3: card/item headings
   - Body: readable at 16-18px
   - Small: labels, captions, meta text
   - All in Dutch. All realistic for the business type.

6. CTA ARCHITECTURE — from Prompt 1:
   - Primary CTA button style consistent across the page (color, shape, size)
   - Secondary CTA as ghost/outline button
   - Sticky mobile CTA bar at bottom (fixed position)
   - Form section with the recommended field count and button text

7. TRUST SIGNALS — from Prompt 1 priority ranking:
   - Place top trust signals in/near the hero
   - Distribute remaining trust signals in appropriate sections
   - Use realistic Dutch trust content (review scores, certification names, "jaar ervaring" numbers)

8. RESPONSIVE — the HTML should look correct at:
   - Desktop: 1440px (primary design target)
   - Tablet: 768px (graceful grid collapse)
   - Mobile: 375px (single column, touch-friendly CTAs)
   Use CSS media queries or container-based responsive rules.

9. SELF-CONTAINED — the HTML file must work when opened directly in a browser:
   - Inline all CSS in a <style> tag (or use Tailwind CDN play script if the layout is complex)
   - Load fonts via Google Fonts CDN <link> tags
   - Use placeholder image URLs (e.g., via picsum.photos or colored divs with labels like "[Team foto]")
   - No external JS dependencies

10. ANTI-GENERIC CHECKLIST — before saving, verify:
    [ ] No two adjacent sections have the same background color
    [ ] Section padding values are NOT all the same
    [ ] At least one grid uses asymmetric column spans
    [ ] At least one decorative SVG or shape element exists
    [ ] At least one section breaks the standard container width
    [ ] Cards within a section are NOT all identical in size/layout
    [ ] The hero has at least 3 visual layers (text, image/shape, decorative element)
    [ ] Every visual choice traces to a reference source (archetype, competitor, craft library)

Save as `homepage-reference.html` in the project root.

After generating, list:
- Which visual craft library elements were used and where
- Which competitor patterns inspired each section
- Which archetype blueprint decisions drove the section order and CTA placement
```

-> HUMAN: Open `homepage-reference.html` in browser. Review the full page. If changes are needed, tell Claude specific adjustments (e.g., "darker footer", "hero needs more contrast", "services section should use editorial layout not cards", "more whitespace between sections 3 and 4"). Claude edits the existing HTML file — no full regeneration. Iterate until satisfied.

---

### Prompt 5 — Extract Design System (DESIGN.md)

```
Read the following:
- homepage-reference.html (the approved visual reference)
- Prompt 1 output (archetype, tone scores, CTA architecture, trust signals, pricing display)
- Prompt 3c output (effects list, layout suggestions)
- C:\Users\yanni\Hub\business\sops\reference-effects-library.md (for effect code references)

Analyze homepage-reference.html and extract ALL design tokens into DESIGN.md.

DESIGN.md must contain these sections in this order:

## 1. Project Identity
- Client name, business type, archetype letter + name
- Visual tone scores (energy, density, formality, richness, animation)
- Brand assets (logo, colors, fonts — what the client provided vs what we chose)
- Addressal: je/jij or u/uw (with justification from sub-variant check)
- Target audience summary (from Prompt 1)

## 2. Color System
Extract from homepage-reference.html every color used. Document as:
- Role (primary, secondary, accent, background, surface, surface-elevated, text, text-muted, border, error, success)
- Hex value
- Where used (e.g., "hero background, footer background, dark section bg")
- WCAG contrast ratio against its most common pairing

## 3. Typography
Extract from homepage-reference.html:
- Heading font: family, weights used, Google Fonts import URL
- Body font: family, weights used, Google Fonts import URL
- Type scale: H1 through H6 sizes (px and rem), line-heights, letter-spacing
- Body text size, line-height
- Small/caption text size
- Font loading strategy recommendation (display: swap)

## 4. Spacing System
Extract from homepage-reference.html:
- Section padding values (list each section with its exact pt/pb/py)
- Container max-widths used
- Grid gaps
- Component internal padding (cards, buttons, form fields)
- Vertical rhythm between elements within sections

## 5. Component Styles
Extract from homepage-reference.html:
- Button styles: primary (bg, text, border-radius, padding, hover state), secondary/ghost, sizes
- Card styles: background, border-radius, shadow, padding, hover state
- Form field styles: border, border-radius, padding, focus state, label positioning
- Badge/pill styles
- Nav link styles (normal, hover, active)
- Any other recurring component patterns

## 6. Grid & Layout
Extract from homepage-reference.html:
- Grid column structures per section (e.g., "hero: 7/5 split", "services: 4/4/4 with first card spanning 8")
- Breakpoint behavior (what changes at 1024px, 768px, 640px)
- Container strategy (max-width values, when full-bleed is used)
- Which sections break the container

## 7. Decorative Elements
List every visual craft element used in homepage-reference.html:
- Element name (from visual craft library)
- Where placed
- Color values used
- SVG code or CSS snippet (so builders can reproduce exactly)

## 8. Design Suggestions
The layout suggestions chosen in Prompt 3c (L1-L4, C1-C4, V1-V4 selections).
Include the specific competitor patterns we decided to incorporate.
These guide Claude Code during the build phase.

## 9. Animation Specification
- Animation level (from archetype)
- Approved effects list (from Prompt 3c Part C)
- Performance budget (from effects library)
- Which effects apply to which sections
- Reduced-motion fallback requirement

## 10. CTA Architecture
- Primary contact method + button text
- Secondary contact method + button text
- Form fields (count, names, types, placeholder text)
- Sticky mobile CTA bar: yes/no, content
- CTA placement per section
- Multi-step form structure if applicable (from conversion patterns)

## 11. Trust Signals
- Priority ranking (top 3 from Prompt 1)
- Placement per section
- Specific content (review score, certification names, experience years, guarantee text)

## 12. Pricing Display
- Approach: full/range/hidden (from archetype)
- Format: Dutch conventions (EUR X,- or vanaf EUR X)
- Where displayed (which sections)
- BTW note requirement

## 13. Anti-Patterns (NEVER DO)
- Do not add max-w-*, mx-auto, or container wrappers not in the reference HTML
- Do not normalize padding/margin values across sections
- Do not symmetrize asymmetric layouts
- Do not use only fade-in-up animation
- Do not use stock photography for team/project images
- Do not use "Versturen" as form button text
- Do not use aggressive sales language
- Do not use countdown timers or fake urgency
- Do not use visible CAPTCHA
- Do not mix je/u on the same site
- Do not set hero elements to opacity: 0 (GSAP-managed elements must have opacity: 1 by default)

## 14. Dutch UX Requirements
- Number format: 1.234,56
- Currency: EUR 49,- or EUR 49,95 (EUR + space + amount)
- Date: "15 maart 2025"
- Phone: 06-12345678 or area code format
- Postcode: 1234 AB
- Cookie banner: required, Dutch text
- Legal footer: KVK-nummer, BTW-nummer
- Hyphens: enable `hyphens: auto` with `lang="nl"` for long compound words
- Trailing slashes: ALL internal links end with `/`

## 15. Design Reference
- `homepage-reference.html` is the visual reference for layout, spacing, and visual intent
- `DESIGN.md` is the token source of truth for exact values
- During builds: when in doubt about layout, reference the HTML. When in doubt about a value, reference DESIGN.md.
- `competitor-reference/*.html` files show professional patterns to maintain quality parity

Save as `DESIGN.md` in the project root.

Then commit everything:
git add DESIGN.md homepage-reference.html color-options.html typography-options.html layout-options.html COMPETITORS.md competitor-reference/
git commit -m "design: complete Session 1 design direction"
```

-> HUMAN: Review DESIGN.md. Confirm or request changes. Once approved, Session 1 is complete. Proceed to Session 2 (Content & Copywriting).
