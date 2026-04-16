# Neem gerust contact op

> **URL**: `/contact/`
> **Primary keyword**: `contact schoonmaakbedrijf betuwe`
> **Secondary keywords**: `offerte schoonmaak rivierenland`, `schoonmaakbedrijf buren contact`
> **Search intent**: Transactional / Navigational
> **Page type**: Conversion — minimal copy, maximum action
> **Created**: 27 maart 2026

---

## Meta

**Title**: `Contact | John's Schoonmaakbedrijf Buren`
**Description**: `Neem contact op met John's Schoonmaakbedrijf in Buren. Bel, WhatsApp of vraag een offerte aan. Reactie binnen 2 werkuren.`

---

## H1

```
Neem gerust contact op
```
*Particle*: gerust ✓

---

## Intro

```
Wil je weten wat wij voor je bedrijf kunnen doen? Bel ons,
stuur een bericht of vul het formulier in. Binnen 2 werkuren
hoor je van ons.
```
*Word count*: 27 words ✓ (target: 20-40)

---

## Contactgegevens

### Bellen

```
06 23545276
```
Link: `tel:0623545276`
Label: Bellen
Sublabel: Direct contact met John

### WhatsApp

```
06 23545276
```
Link: `https://wa.me/31623545276`
Label: WhatsApp
Sublabel: Stuur een bericht

### E-mail

```
info@johnsschoonmaakbedrijf.nl
```
Link: `mailto:info@johnsschoonmaakbedrijf.nl`
Label: E-mail
Sublabel: We reageren binnen 2 werkuren

---

## Adres en bereikbaarheid

```
John's Schoonmaakbedrijf
[Straatnaam + huisnummer]
4116 XX Buren
Gelderland
```

> **[PLACEHOLDER]** Vul het exacte adres in. Postcode 4116 is
> het postcodegebied van Buren.

### Bereikbaar

```
Maandag t/m vrijdag: 07:00 – 18:00
Zaterdag en zondag: gesloten
```

> Schoonmaakwerkzaamheden worden ook buiten deze uren uitgevoerd,
> afhankelijk van de afspraken met de klant.

### Bedrijfsgegevens

| Gegeven | Waarde |
|---|---|
| KvK | [nummer invullen] |
| BTW | [NL-nummer invullen] |

---

## Offerte formulier

### Heading
```
Offerte aanvragen
```

### Subtext
```
Vul het formulier in. We reageren binnen 2 werkuren.
```
> *Origineel DESIGN.md had em dash ("—") in deze zin. Vervangen
> door punt conform anti-AI copyrichtlijn.*

### Fields

| # | Label | Name | Type | Placeholder | Required |
|---|---|---|---|---|---|
| 1 | Voornaam | `voornaam` | text | Jan | ✓ |
| 2 | Achternaam | `achternaam` | text | de Vries | ✓ |
| 3 | Bedrijfsnaam | `bedrijf` | text | Je bedrijfsnaam | ✓ |
| 4 | E-mailadres | `email` | email | jan@bedrijf.nl | ✓ |
| 5 | Telefoonnummer | `telefoon` | tel | 06-12345678 | |
| 6 | Gewenste dienst | `dienst` | select | Selecteer een dienst | |
| 7 | Toelichting | `bericht` | textarea | Vertel kort over je locatie, oppervlak en gewenste frequentie... | |

**Layout**: Row 1 = voornaam + achternaam (2-col). Row 2 = bedrijfsnaam (full). Row 3 = email + telefoon (2-col). Row 4 = dienst (full). Row 5 = toelichting (full). ≤768px: single column.

**Required indicator**: Rood sterretje `*` na label

### Select options (Gewenste dienst)

| Value | Label |
|---|---|
| kantoorschoonmaak | Kantoorschoonmaak |
| glazenwassen | Glazenwassen |
| bouw-oplevering | Bouw-oplevering |
| anders | Anders of combinatie |

### Submit button

```
Offerte aanvragen
```
Style: `btn-primary`, full-width, arrow icon
**Never**: "Versturen" or "Submit"

### Privacy note

```
Wij gebruiken je gegevens alleen om contact met je op te nemen.
Lees ons privacybeleid.
```
Link: [privacybeleid](/privacybeleid/)
Style: font-size 11px, centered, text-light color

---

## Google Maps

```
[Google Maps embed placeholder]
Locatie: Buren, Gelderland
Coördinaten: circa 51.9117° N, 5.3356° O
```

> Embed code wordt toegevoegd tijdens de Astro build. Gebruik
> `loading="lazy"` en `title="Locatie John's Schoonmaakbedrijf
> in Buren"` op het iframe.

---

## Werkgebied vermelding

```
We zijn actief in de hele Betuwe en Rivierenland. Denk aan
Buren, Tiel, Culemborg, Geldermalsen, Elst en omstreken.
```

> Korte vermelding onder de kaart of contactgegevens. Verwijst
> naar toekomstige werkgebiedpagina's (later session).

---

## Internal links

- [Diensten](/diensten/) — in footer of na werkgebied vermelding
- [Over ons](/over-ons/) — "Meer weten over ons?"
- [FAQ](/faq/) — "Veelgestelde vragen"

---

## Anti-AI check

| Check | Status |
|---|---|
| Particle in H1 | ✓ gerust |
| No em dashes | ✓ replaced with period in form subtext |
| No "Versturen" | ✓ "Offerte aanvragen" used |
| je/jij consistent | ✓ "Je bedrijfsnaam", "je gegevens", "je locatie" |
| Phone format | ✓ 06 23545276 (per DESIGN.md §14) |
| Postcode format | ✓ 4116 XX (XXXX XX with space) |
| Email lowercase | ✓ |
| Trailing slashes | ✓ all internal links end with / |
| KvK/BTW placeholder | ✓ marked for completion |

**Total prose word count**: ~100 words (conversion page — intentionally minimal)
