# UI/UX Audit - John's Schoonmaakbedrijf Website

> Audit based on:
> - Reference site: [johnsglazenwassersbedrijf.knapgemaakt.nl](https://johnsglazenwassersbedrijf.knapgemaakt.nl/)
> - UI/UX Pro Max design system recommendations
> - UX guidelines (accessibility, touch, forms, landing patterns)

---

## Part 1: What the Glazenwassersbedrijf Site Does Well (and we should adopt)

The glazenwasser site is already live and functional. Several patterns there should inform improvements to our schoonmaakbedrijf build.

### 1.1 "Bereken je prijs" as primary CTA
The glazenwasser site uses "Bereken je prijs" (Calculate your price) as the primary CTA. While our schoonmaakbedrijf uses "Offerte aanvragen" (which is correct for B2B since there is no standardized pricing), the glazenwasser site places this CTA in **three locations**: nav, hero, and page bottom. Our implementation already does this, so we're aligned.

### 1.2 WhatsApp as contact channel
The glazenwasser site offers WhatsApp alongside phone and email. Our schoonmaakbedrijf site currently only has phone + email. WhatsApp is increasingly expected by Dutch business contacts, especially smaller businesses.

**Action: Add WhatsApp link to header top bar, footer, and mobile sticky bar.**

### 1.3 Google Reviews integration (4.5/5 sterren)
The glazenwasser site displays a Google Reviews badge with "4.5/5 Sterren" prominently. Our site has placeholder testimonials but no platform-backed review score.

**Action: Add a Google Reviews badge/link when reviews are collected. Prepare the design for it now.**

### 1.4 "100% tevredenheidsgarantie" badge
The glazenwasser site prominently displays a satisfaction guarantee. Our schoonmaakbedrijf site has no guarantee. From our research, this was identified as a key differentiator that 0/10 local competitors use.

**Action: Add "Niet tevreden? Wij komen gratis terug" guarantee badge to the homepage.**

### 1.5 Real photography in WebP format
The glazenwasser site uses real team/service photos in optimized WebP format with descriptive alt text. Our site has placeholder divs. This is expected (photos will come), but the code should be ready for optimized WebP images.

**Action: Ensure image placeholders have proper alt text structure ready.**

### 1.6 Service cards with images
The glazenwasser site shows 8 service cards each with a real photo + title + description + "Lees meer" link. Our service cards use icons only. Adding image placeholders to service cards would create a more compelling visual.

**Action: Add image placeholder area to service cards.**

### 1.7 Location pages in footer
The glazenwasser site links to 5 specific municipality pages (Tiel, Geldermalsen, Culemborg, Meteren, Buren) from the footer. Our site shows region tags but doesn't link to dedicated location pages yet.

**Action: Not critical for v1, but worth noting for SEO phase.**

---

## Part 2: UI/UX Pro Max Audit Findings

### 2.1 CRITICAL - Accessibility Issues

| Issue | Current State | Fix Required |
|-------|--------------|--------------|
| **`cursor-pointer` missing** | Service cards, footer links, and CTA links don't have explicit `cursor-pointer` | Add `cursor-pointer` to all `<a>` and `<button>` elements (Tailwind base should handle `<a>` but verify) |
| **`touch-action: manipulation`** | Not set anywhere | Add to `<html>` to eliminate 300ms tap delay on mobile |
| **Form error states** | Contact form has no error messaging, no `aria-live` region, no validation feedback | Add `aria-live="polite"` error container, inline validation on blur |
| **Form submit feedback** | No loading state on form button, no success/error message after submit | Add loading spinner in button, success confirmation message |
| **`prefers-reduced-motion`** | Not respected anywhere | Add `@media (prefers-reduced-motion: reduce)` to disable transitions |
| **Alt text on placeholder images** | Placeholder divs have no meaningful alt text | Add descriptive alt attributes ready for real images |
| **Focus styles on mobile sticky bar** | Not explicitly styled | Ensure `:focus-visible` works on mobile CTA buttons |

### 2.2 HIGH - Touch & Interaction

| Issue | Current State | Fix Required |
|-------|--------------|--------------|
| **Touch target sizing** | Mobile menu hamburger is `p-2` (may be <44px) | Ensure minimum `min-h-[44px] min-w-[44px]` on all touch targets |
| **Touch spacing** | Mobile menu items have `py-3` (good) but check actual pixel sizes | Verify 44px minimum height and 8px gaps |
| **Mobile sticky bar bottom padding** | Content may be hidden behind the fixed bottom CTA bar | Add `pb-16 md:pb-0` to `<main>` or `<body>` to prevent content being cut off |

### 2.3 HIGH - Layout & Performance

| Issue | Current State | Fix Required |
|-------|--------------|--------------|
| **No `prefers-color-scheme` handling** | Site is light-only, which is fine, but favicon should handle dark mode | Update favicon SVG for dark system theme |
| **Font loading optimization** | Using `display=swap` (good) but no `font-display` fallback metrics | Consider adding `size-adjust` for CLS prevention |
| **Missing `<meta name="theme-color">`** | Not present in `<head>` | Add `<meta name="theme-color" content="#0A2F38">` for mobile browser chrome |
| **Missing Open Graph meta tags** | No `og:title`, `og:description`, `og:image` | Add OG tags for social sharing |

### 2.4 MEDIUM - Visual & Design Refinements

| Issue | Current State | Fix Required |
|-------|--------------|--------------|
| **No "tevredenheidsgarantie" section** | Missing entirely | Add guarantee badge/section between testimonials and service area |
| **No WhatsApp contact option** | Only phone and email | Add WhatsApp link (same number: 06 23545276) |
| **Service cards lack image area** | Icons only | Add image placeholder div above icon for future photos |
| **Testimonial section has no review platform link** | Standalone quotes only | Add "Bekijk onze reviews op Google" link (prepare for when reviews exist) |
| **Footer lacks social links** | No social media links | Add placeholder for LinkedIn/Facebook when available |
| **No FAQ section on homepage** | Missing | Add FAQ accordion with Schema.org FAQPage markup for SEO |
| **`<details>` element in ServiceArea** | Native `<details>` has no transition | Consider keeping it (functional) or note as acceptable for "solid/still" design direction |

### 2.5 MEDIUM - Form UX

| Issue | Current State | Fix Required |
|-------|--------------|--------------|
| **No inline validation** | Form validates only on submit (browser default) | Add blur-based validation for required fields |
| **No character feedback** | Textarea has no max length or character count | Add `maxlength` attribute |
| **Select has placeholder option** | `<option value="">Selecteer een dienst (optioneel)</option>` is selectable | Add `disabled selected` to placeholder option |
| **No autocomplete attributes** | Form inputs lack `autocomplete` hints | Add `autocomplete="name"`, `autocomplete="email"`, etc. |
| **Submit button has no loading state** | Static button text always | Add disabled + spinner state during form submission |

### 2.6 LOW - Polish & Details

| Issue | Current State | Fix Required |
|-------|--------------|--------------|
| **Heading font in CSS comment** | Comment says "Plus Jakarta Sans" but verify it's loading | Confirmed in Layout.astro Google Fonts link - OK |
| **`line-length` check** | Body text max-width not explicitly set everywhere | Verify prose sections don't exceed 75ch on wide screens |
| **z-index scale** | Using `z-50` (header) and `z-40` (mobile bar) | Document scale: 40 (mobile bar) < 50 (header) - OK |
| **Consistent border-radius** | Mix of `rounded-lg`, `rounded-xl`, `rounded-2xl`, `rounded-full` | Audit for consistency per element type |

---

## Part 3: Changes Prioritized

### Must Fix Before Launch (Critical/High)

1. **Add `touch-action: manipulation` to html element** - eliminates 300ms mobile tap delay
2. **Add `prefers-reduced-motion` media query** - accessibility requirement
3. **Add bottom padding on mobile for sticky bar** - content currently hidden behind it
4. **Add `<meta name="theme-color">` and Open Graph tags** - missing meta
5. **Fix form: `autocomplete` attributes, select `disabled`, `aria-live` error region**
6. **Ensure 44px minimum touch targets** on hamburger button and mobile nav
7. **Add `cursor-pointer`** to service cards (they're `<a>` tags so should be OK, but verify)

### Should Fix (Medium - improves quality)

8. **Add WhatsApp contact** to header top bar, footer, mobile sticky bar
9. **Add guarantee section** ("Niet tevreden? Wij komen gratis terug.")
10. **Add FAQ section** to homepage with FAQPage schema markup
11. **Add Google Reviews placeholder** (badge design ready for when reviews come)
12. **Add image placeholder area** to service cards for future photography
13. **Improve form UX** - blur validation, submit loading state, success message
14. **Add social media link placeholders** in footer

### Nice to Have (Low)

15. **Add `size-adjust` to font-face** for CLS prevention
16. **Audit `border-radius` consistency** across components
17. **Add `max-width: 75ch`** to prose text blocks
18. **Favicon dark mode** support

---

## Part 4: Design System Alignment Check

The UI/UX Pro Max tool recommended "Trust & Authority" style with navy (#0F172A) primary. Our implementation uses deep teal (#1B7A8A) which is a deliberate deviation to avoid the generic blue/navy that 70% of local competitors use. This deviation is justified by our research findings.

| Recommendation | Our Implementation | Status |
|----------------|-------------------|--------|
| Certificates/badges displayed | VCA badge in hero, footer, service sidebars | Aligned |
| Expert credentials | 17 years experience, team names, roles | Aligned |
| Case studies with metrics | Placeholder testimonials only | Gap - needs real content |
| Before/after comparisons | Not present | Gap - consider for service pages when photos come |
| Industry recognition | VCA only | OK for now |
| WCAG AAA contrast | Needs verification | Verify primary-900 text on white, white on primary-900 |
| Badge hover effects | Not present (aligned with "solid/still" design direction) | Acceptable |
| No playful design | Correct - design is steady and professional | Aligned |
| No AI gradients | Correct - no gradients used | Aligned |

---

## Part 5: Summary

The current build is structurally sound and follows the design direction well. The most impactful improvements are:

1. **Accessibility fixes** (touch-action, reduced-motion, form ARIA) - these are requirements, not nice-to-haves
2. **WhatsApp integration** - the glazenwasser site already has it, and it's expected in the Dutch market
3. **Guarantee section** - "Niet tevreden? Wij komen gratis terug" is a zero-cost differentiator
4. **FAQ section with schema** - boosts SEO and addresses visitor questions inline
5. **Mobile bottom padding** - the sticky CTA bar currently covers content

All changes are additive. No structural rewrites needed.
