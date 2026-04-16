# Session 2 — Content & Copywriting

> Separate session from Session 1. ~45 minutes. Output: CONTENT/ folder
> Input: DESIGN.md (from Session 1)
> Skills: none specific
> MCPs: none

## Prerequisites

- Session 1 complete: DESIGN.md + homepage-reference.html committed
- Client business data available (services list, phone, email, address, certifications, opening hours, team info)

## Prompts

### Prompt 1 — Context Loading + Sitemap + Keywords

```
Read the following files before doing anything else:
- DESIGN.md (in project root)
- COMPETITORS.md (in project root)
- CLAUDE.md (in project root)
- C:\Users\yanni\Hub\business\sops\reference-anti-ai-dutch-copywriting.md

From DESIGN.md, extract and confirm: tone of voice, homepage section order, CTA architecture (button texts, form heading, form subtext), trust signals, je/jij vs u setting, pricing approach.

The anti-AI Dutch copywriting guide is the red thread for ALL copy in this session. Every prompt that follows must apply its rules — the find-and-replace table (Task 2), the red/green flag checklist (Task 6), and the voice guide for this business type (Task 7). Confirm you have read and understood it.

SCOPE FOR THIS SESSION:
- Core pages only: homepage, service pages, about, contact, FAQ, legal
- Location pages (werkgebied/[stad]) are a later session — note them in sitemap as "later session" and skip
- Schema markup, technical SEO optimization are a later session

Now define the sitemap and keyword targets for this website.

SITEMAP DEFAULTS BY ARCHETYPE:

Archetype A (Urgent Response — loodgieter, elektricien, dakdekker, installateur):
- Homepage
- Diensten (overview) + individual service pages
- Over ons
- Werkgebied / Service area
- Contact
- FAQ (can be section on homepage + dedicated page)
- Blog (optional — for SEO long-tail)
- Privacy + Algemene voorwaarden

Archetype B (Visual Portfolio — hovenier, schilder, bouwbedrijf, interieurontwerper):
- Homepage
- Diensten (overview) + individual service pages
- Portfolio / Projecten (overview + individual project pages)
- Over ons
- Werkgebied / Service area
- Contact
- FAQ
- Blog (recommended — for SEO)
- Privacy + Algemene voorwaarden

Archetype C (Experience & Atmosphere — restaurant):
- Homepage
- Menu / Menukaart
- Over ons / Het verhaal
- Reserveren
- Contact
- Privacy + Algemene voorwaarden

Archetype D (Clinical Trust — fysiotherapeut, tandarts):
- Homepage
- Behandelingen (overview + individual treatment pages)
- Team / Ons team (individual practitioner pages)
- Tarieven & vergoedingen
- Afspraak maken
- Over de praktijk
- FAQ
- Contact
- Privacy + Algemene voorwaarden

Archetype E (Lifestyle & Personal Brand — kapper, PT, makelaar, schoonmaak):
- Homepage
- Diensten + pricing
- Over ons / Over [naam]
- Reviews / Ervaringen
- Contact
- FAQ
- Blog (optional)
- Privacy + Algemene voorwaarden

Based on the archetype and this client's specific services, create the final sitemap. For each page list:
- Page name (Dutch)
- URL slug (lowercase, hyphens, trailing slash)
- Primary purpose
- Primary keyword target
- Secondary keywords (2-3 natural variations)
- Search intent (informational / transactional / navigational)
- AI SEO opportunity: what question could this page answer in AI Overviews?

Also define the internal linking plan:
- Which pages link to which? (every key page within 3 clicks of homepage)
- Anchor text suggestions (50-60% partial-match, 35-45% branded/generic, max 10% exact-match)

Location pages: note them as "later session — template to be created" and move on.

Save as CONTENT/sitemap.md.
```

---

### Prompt 2 — Homepage Copy

```
Read DESIGN.md sections 5 (Homepage Section Order), 6 (Hero Specification), 9 (CTA Architecture), 10 (Trust Signals), 11 (Pricing Display), and 14 (Dutch UX Requirements).
Read CONTENT/sitemap.md for keyword targets.

Write all homepage copy. Follow these rules strictly:

DUTCH COPY RULES:
- Language: use je/jij (check DESIGN.md section 1 for exceptions)
- Headline max: 7 words / 50 characters
- Subtext: 15-25 words
- CTA button text: max 20 characters (use exact text from DESIGN.md section 9)
- Body paragraphs: 3-5 lines, 8-10 words per sentence
- Reading level: B1 (Coolblue standard — simple, direct, conversational)
- Subheading every 50-75 words
- Never open with "Welkom op onze website"
- Never use superlatives ("beste", "#1", "marktleider")
- Never use em dashes (—) — not used in Dutch writing. Use comma, period, or colon instead.
- Never use "echter", "tevens", "desalniettemin" — AI-tell formal words. Use "maar", "ook", "toch".
- Apply ALL rules from the anti-AI Dutch copywriting guide (find-and-replace table, red/green flags, voice guide)
- Copy should sound like the business owner talking to a customer on the phone — natural, direct, knowledgeable
- Start every section with the conclusion/benefit, not the explanation
- Use "scanbaar schrijven" — inverted pyramid, meaningful subheadings, bold key phrases

AI SEO RULE:
- Start the page with a direct answer paragraph (40-60 words) that answers the primary keyword question. This goes in the hero subtext or immediately below the hero.
- H2 headings should use question format where natural ("Waarom [service]?" rather than "Onze voordelen")

FOR EACH SECTION in the homepage order from DESIGN.md, write:
1. Section heading (H2) — max 5 words / 35 chars
2. Section subheading or intro (if applicable) — max 25 words
3. Section body copy — follow word limits per section type:
   - Hero headline: max 7 words / 50 chars
   - Hero subtext: 15-25 words
   - Service descriptions: 12-20 words each
   - Process steps: 10-15 words per step
   - About section: 80-150 words (2-3 paragraphs)
   - Testimonial placeholders: "[Klant naam] — [Bedrijf/Locatie]" (real reviews added later)
   - CTA section: 15-25 words supporting text
4. Any micro-copy (button text, labels, badges)

Save as CONTENT/homepage.md with clear section markers matching DESIGN.md section order.
```

---

### Prompt 3 — Service Page Copy

```
Read DESIGN.md and CONTENT/sitemap.md.

For each service/subpage in the sitemap (these may be called diensten, behandelingen, programma's, collecties, or any other category depending on the business type), write the full page copy. Each page follows this structure:

1. H1: "[Page naam]" — includes primary keyword naturally
2. Direct answer paragraph (40-60 words): immediately answers "wat is [onderwerp]" or "wat kost [onderwerp]" — front-loaded for AI citation
3. Description (150-250 words): what it includes, how it works, who it's for
4. Why choose us (3-4 bullet points): specific to THIS page topic, not generic company USPs
5. Process: how this specific service is delivered (3-5 steps)
6. Pricing (if DESIGN.md says to show): "vanaf" pricing or price range per DESIGN.md section 11
7. FAQ (3-5 questions specific to this service): question-format, answering real customer questions
   - Include the primary keyword naturally in at least one question
   - Answers: 30-60 words each, direct and factual
8. CTA: specific call-to-action for this service (use CTA text from DESIGN.md section 9)

COPY CONSTRAINTS:
- Total page word count: 400-800 words (enough for SEO, not walls of text)
- Keyword density: 0.5-2% for primary keyword (3-6 natural mentions in 600 words)
- Include 2-3 internal links to other relevant pages (services, contact, about)
- Don't repeat the exact same USP copy on every service page — make each page unique
- Apply ALL anti-AI Dutch copywriting rules

Save each service page as CONTENT/diensten/[service-slug].md.
```

---

### Prompt 4 — About + Contact Pages

```
Read DESIGN.md sections 9 (CTA Architecture) and 14 (Dutch UX Requirements).

Write TWO pages:

--- ABOUT PAGE (CONTENT/over-ons.md) ---

Structure:
1. H1: "Over [Bedrijfsnaam]" or a warmer variant
2. Opening paragraph (50-80 words): who you are, what you do, where you're based. Direct, personal, not corporate.
3. The story (100-150 words): how the business started, why, what drives the owner. Make it feel like meeting a neighbor — warm, authentic, "nuchter."
4. Team section (if applicable): name, role, one personal detail per person. Photo placeholders with alt text descriptions.
5. Certifications/credentials: list with brief explanation of what each means for the customer (not just badge names)
6. Values/approach (3-4 points): what makes working with this business different. Use concrete examples, not corporate values.
7. CTA: "Benieuwd wat we voor je kunnen betekenen?" + primary CTA button

Tone:
- Most personal page on the site
- Use first person ("ik"/"wij") naturally
- Include specific details: years of experience, number of projects, specific expertise
- Sound like someone explaining their work at a verjaardag, not a LinkedIn bio
- If one owner: use "ik" and make it personal. If a team: use "wij" but still name people.

--- CONTACT PAGE (CONTENT/contact.md) ---

Structure:
1. H1: warm invitation, not just "Contact" (e.g., "Neem contact met ons op" or "Laten we kennismaken")
2. Intro (20-40 words): one sentence about what happens when they reach out
3. Contact form:
   - Heading: exact text from DESIGN.md section 9 (form heading)
   - Subtext: exact text from DESIGN.md section 9 (form subtext)
   - Field labels: Naam, Telefoon, E-mail, [dropdown if specified], Uw bericht
   - Button text: exact from DESIGN.md section 9 (NEVER "Versturen")
   - Privacy note below form: "Wij gebruiken je gegevens alleen om contact met je op te nemen. Lees ons privacybeleid."
4. Direct contact info:
   - Phone (clickable)
   - Email
   - WhatsApp (if in CTA architecture)
   - Address: [straat], [postcode] [stad]
   - KvK: [nummer]
5. Opening hours (if applicable)
6. Google Maps embed placeholder (address for the embed)

Keep the contact page minimal — it exists to convert, not to inform.

Save as CONTENT/over-ons.md and CONTENT/contact.md.
```

---

### Prompt 5 — FAQ

```
Read DESIGN.md and all service page copy in CONTENT/diensten/.

Create a comprehensive FAQ page with 8-12 questions. This page is critical for AI SEO — pages with FAQ schema earn significantly more AI citations.

QUESTION SOURCING:
- Include the top questions from each service page FAQ (don't duplicate — link to service page for details)
- Add general business questions:
  - "Wat kost [primary service]?" (pricing question — #1 AI Overview trigger for local businesses)
  - "In welke regio zijn jullie actief?" (service area)
  - "Hoe snel kunnen jullie beginnen?" (timeline/availability)
  - "Zijn jullie verzekerd?" (trust)
  - "Hoe vraag ik een offerte aan?" (process)
  - [Industry-specific question based on archetype]

ANSWER FORMAT (optimized for AI citation):
- First sentence: direct answer to the question (this is what AI extracts)
- Following 2-3 sentences: supporting detail, specifics, context
- Total per answer: 40-60 words
- Include the question's keyword naturally in the answer
- Use concrete numbers where possible (prices, timeframes, counts)

FAQ FORMAT:
## Veelgestelde vragen

### Wat kost [service]?
[Direct answer first.] [Supporting detail.] [Specific example or range.]

### Hoe snel kunnen jullie beginnen?
[Direct answer.] [Supporting detail.]

This format maps directly to FAQPage schema in a later session.

Save as CONTENT/faq.md.
```

---

### Prompt 6 — Legal Pages

```
Create standard legal pages in Dutch. These are required by Dutch law.

1. Privacyverklaring (Privacy Policy):
   - Company details (naam, adres, KvK, e-mail)
   - What data is collected (contact form submissions, analytics)
   - Legal basis: legitimate interest for contact forms, consent for analytics cookies
   - How data is stored and for how long
   - Rights of the user (inzage, correctie, verwijdering, bezwaar)
   - Cookie usage (refer to cookie banner)
   - Contact for privacy questions
   - Last updated date

   Use clear, simple Dutch — not legal jargon. "Wij slaan je naam en e-mailadres op zodat we je aanvraag kunnen beantwoorden" not "De verwerkingsverantwoordelijke verwerkt persoonsgegevens conform de AVG."

2. Algemene voorwaarden (Terms of Service):
   - Only if the client provides services through the website
   - Keep simple for small businesses
   - Include herroepingsrecht (14-day withdrawal right for online bookings)

Save as CONTENT/privacy.md and CONTENT/algemene-voorwaarden.md.
```

---

### Prompt 7 — Meta Tags

```
Read CONTENT/sitemap.md with keyword targets, and all page copy files in CONTENT/.

For each page, draft the meta title and description.

TITLE RULES:
- 50-60 characters max
- Primary keyword near the beginning (front-loaded)
- Brand name at the end: "| [Bedrijfsnaam]"
- Include differentiator where space allows (price, speed, guarantee)

DESCRIPTION RULES:
- 140-155 characters
- Include primary keyword (will be bolded in Google)
- Lead with strongest benefit or value proposition
- Include call-to-action ("Vraag een offerte aan", "Bel ons", etc.)

FORMAT:
## Homepage
Title: [Schoonmaakbedrijf Buren | Kantoren & Bedrijven | Bedrijfsnaam]
Description: [Professioneel schoonmaakbedrijf in Buren. Kantoren, bedrijfshallen, VCA-gecertificeerd. Vraag een vrijblijvende offerte aan.]
H1: [from homepage copy]

## Diensten — [Service naam]
Title: [...]
Description: [...]
H1: [from service page copy]

Save as CONTENT/meta-tags.md.
```

---

### Prompt 8 — Content Review

```
Read all files in the CONTENT/ folder.

Self-audit all copy against this checklist:

- [ ] All hero headlines are 7 words / 50 characters or fewer
- [ ] All CTA button texts match DESIGN.md section 9 exactly
- [ ] All body text uses je/jij consistently (no mixing with u, unless DESIGN.md specifies u)
- [ ] No superlatives ("beste", "#1", "marktleider") anywhere
- [ ] No "Welkom op onze website" or similar generic openings
- [ ] No em dashes used English-style
- [ ] No AI-tell words from the anti-AI copywriting guide (Task 2 find-and-replace table)
- [ ] No "In een wereld waar..." or similar AI openers
- [ ] No Oxford commas
- [ ] No title case in headings
- [ ] Every page has at least one direct answer paragraph in the first 100 words
- [ ] Every H2 on service pages uses question format where natural
- [ ] FAQ answers start with a direct answer sentence
- [ ] All Dutch formatting correct (comma decimals, period thousands, euro symbol before amount)
- [ ] Internal links present (at least 2-3 per page pointing to other pages)
- [ ] Pricing display matches DESIGN.md section 11 approach
- [ ] KvK, BTW-ID, address present on contact page and footer
- [ ] Privacy page references correct company details
- [ ] Total word count per page is within range (400-800 for service pages, 300-500 for about/contact)
- [ ] No English words or phrases that should be Dutch
- [ ] No placeholders left unfilled (except photo placeholders and real review placeholders)
- [ ] Phone number format: 06-12345678 or local area code
- [ ] Postcode format: 1234 AB

Create a summary:
- Total pages: [X]
- Total word count: [X]
- Issues found: [list]
- Content ready for build session: [yes/no]

If issues found, fix them. When all checks pass, confirm content is ready.
```

-> HUMAN: Review all CONTENT/ files. Optionally send to client for approval before Session 3.
