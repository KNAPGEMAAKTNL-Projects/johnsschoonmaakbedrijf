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

## Verification Required (never auto-populate)
These claims MUST be confirmed by the client before appearing on the website:
- Certifications (VCA, ISO, Keurmerk Schoon, etc.) — never assume from archetype templates
- Review scores and counts — use exact numbers from the actual review platform
- Years in business ("Sinds 2007" vs "Sinds 2009") — confirm the founding year
- Team size, team structure, named roles — don't imply departments or processes that don't exist
- Service claims (e.g., "milieuvriendelijke producten") — only if confirmed by client
- Any legal identifiers (KvK, BTW) — use exact numbers, not placeholders in production

## Copy Rules
- Never use: "zonder gedoe", "geen gedoe", "scheelt gedoe" — overused AI cliche
- Never use: "Bel ons maar even" — sounds commanding. Use "Bel gerust" instead
- Never use: "Eerlijk" as a selling point — meaningless
- Never use standalone sentence fragments for emphasis ("Grondig." "Echt schoon.")
- Never use generic social proof ("Veel klanten doen het", "De meeste bedrijven kiezen...")
- Don't state the obvious to B2B readers — they already know their problem
- Limit region name ("Betuwe") to SEO elements (title, H1, meta). Remove from body copy and FAQs
- Read `C:\Users\yanni\Hub\business\sops\reference-dutch-copy-research.md` before writing any Dutch copy
- Read `C:\Users\yanni\Hub\business\sops\reference-anti-ai-dutch-copywriting.md` for anti-AI patterns

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
