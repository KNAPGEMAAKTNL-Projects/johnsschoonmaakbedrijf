# Contact

> **URL**: `/contact/`
> **Primary keyword**: `contact schoonmaakbedrijf betuwe`
> **Secondary keywords**: `offerte schoonmaak rivierenland`, `schoonmaakbedrijf buren contact`, `offerte aanvragen schoonmaak`
> **Search intent**: Transactional / Navigational
> **Page type**: Conversion — minimal copy, maximum action
> **Register**: `u / uw`

---

## Meta

**Title**: `Contact | John's Schoonmaakbedrijf`
**Description**: `Neem contact op met John's Schoonmaakbedrijf. Bel 06 23545276, mail of vraag direct een offerte aan. Reactie binnen 2 werkuren.`

---

## H1

```
Neem gerust contact op
```
*John-signature*: verbatim from his `/nieuws/totale-schoonmaakbedrijven` post — "Neem gerust contact met ons op"

---

## Intro

```
Laat weten wat wij voor uw bedrijf kunnen betekenen. Bel
ons, stuur een bericht of vul het formulier in. Binnen 2
werkuren hoort u van ons — persoonlijk, niet via een
callcenter.
```
*Word count*: 31 words ✓
*John-signatures*: `wat we voor uw bedrijf kunnen betekenen` near-verbatim; `niet via een callcenter` as stance (from CLIENT-VOICE)
*Register*: `u / uw` ✓

---

## Contactgegevens

### Bellen

```
06 23545276
```
Link: `tel:0623545276`
Label: Bellen
Sublabel: John neemt meestal zelf op

> **Note**: "John neemt meestal zelf op" is gebaseerd op zijn eigen historische toon en job-ad-signatuur (`Bij interesse contact opnemen met John Hak`). Als dit niet langer standaard is, vervangen door "Persoonlijk contact, geen callcenter".

### E-mail

```
info@johnsschoonmaakbedrijf.nl
```
Link: `mailto:info@johnsschoonmaakbedrijf.nl`
Label: E-mail
Sublabel: Reactie binnen 2 werkuren

> **[PLACEHOLDER]** De huidige schoonmaak-website toont `info@johnsglazenwassersbedrijf.nl` in de footer — vermoedelijk een CMS-vergissing. Voor het nieuwe adres gebruiken wij `info@johnsschoonmaakbedrijf.nl`. John bevestigt welk adres daadwerkelijk gebruikt wordt voor mail.

---

## Adres en bereikbaarheid

### Bezoekadres

```
John's Schoonmaakbedrijf
[Straatnaam + huisnummer]
[Postcode] Buren
Gelderland
```

> **[PLACEHOLDER]** Het bedrijfsadres is Buren (Gelderland) per opgave. Straatnaam, huisnummer en postcode door John aan te leveren. Historisch opereerde het bedrijf vanuit Tricht — operationele vestigingsplaats. Als post naar Buren gaat en operationele basis Tricht blijft, dit op de pagina toelichten.

### Bereikbaar

```
Maandag t/m vrijdag: 07:00 – 18:00
Zaterdag en zondag: gesloten voor telefonisch contact
```

```
Schoonmaakwerk buiten deze uren is uiteraard mogelijk —
voor, tijdens of na kantooruren, in overleg met u als klant.
```
*John-signatures*: `voor, tijdens of na kantooruren` + `in overleg met u als klant` — verbatim twee kernzinnen uit zijn homepage

### Bedrijfsgegevens

| Gegeven | Waarde |
|---|---|
| KvK | [nummer invullen] |
| BTW | — (niet vermeld op verzoek) |

> **[PLACEHOLDER]** KvK-nummer door John aan te leveren. BTW-nummer blijft per zijn instructie voorlopig weg — toe te voegen zodra hij dit wel wil tonen.

---

## Offerte formulier

### Heading
```
Offerte aanvragen
```

### Subtext
```
Laat uw gegevens achter. Wij reageren binnen 2 werkuren.
```

### Fields

| # | Label | Name | Type | Placeholder | Required |
|---|---|---|---|---|---|
| 1 | Voornaam | `voornaam` | text | Jan | ✓ |
| 2 | Achternaam | `achternaam` | text | de Vries | ✓ |
| 3 | Bedrijfsnaam | `bedrijf` | text | Uw bedrijfsnaam | ✓ |
| 4 | E-mailadres | `email` | email | jan@bedrijf.nl | ✓ |
| 5 | Telefoonnummer | `telefoon` | tel | 06-12345678 | |
| 6 | Gewenste dienst | `dienst` | select | Selecteer een dienst | |
| 7 | Toelichting | `bericht` | textarea | Vertel kort over uw pand, oppervlak en gewenst ritme… | |

**Layout**: Row 1 = voornaam + achternaam (2-col). Row 2 = bedrijfsnaam (full). Row 3 = email + telefoon (2-col). Row 4 = dienst (full). Row 5 = toelichting (full). ≤768px: single column.

**Required indicator**: Rood sterretje `*` na label

### Select options (Gewenste dienst)

| Value | Label |
|---|---|
| kantoorschoonmaak | Kantoorschoonmaak |
| glazenwassen | Glazenwassen |
| bouw-oplevering | Opleveringsschoonmaak |
| zonnepanelen | Zonnepanelen reinigen |
| gevelreiniging | Gevelreiniging |
| dakgoten | Dakgoten leegmaken |
| anders | Anders of combinatie |

### Submit button

```
Offerte aanvragen
```
Style: `btn-primary`, full-width, arrow icon
**Never**: "Versturen" of "Submit"

### Privacy note

```
Uw gegevens gebruiken wij alleen om contact met u op te
nemen. Lees ons privacybeleid.
```
Link: [privacybeleid](/privacybeleid/)
Style: font-size 11px, centered, text-light color

---

## Google Maps

```
[Google Maps embed placeholder]
Locatie: Buren, Gelderland
```

> Embed code wordt toegevoegd tijdens de Astro build. Gebruik
> `loading="lazy"` en `title="Locatie John's Schoonmaakbedrijf in Buren"` op het iframe.

---

## Werkgebied vermelding

```
Wij zijn actief in de hele Betuwe en Rivierenland. Panden
in Buren, Tiel, Culemborg, Geldermalsen, Leerdam, Tricht
en omliggende plaatsen bezoeken wij regelmatig. Staat uw
locatie net buiten deze regio? Laat het weten, dan kijken
wij of het past.
```
*Word count*: 37 words
*Regional*: allowed hier omdat het expliciet om werkgebied gaat

> Korte vermelding onder de kaart of contactgegevens. Verwijst naar toekomstige werkgebiedpagina's (later session).

---

## Internal links

- [Diensten](/diensten/) — "Bekijk wat wij doen"
- [Over ons](/over-ons/) — "Meer over ons team"
- [FAQ](/faq/) — "Veelgestelde vragen"

---

## Voice & CLAUDE.md compliance

| Check | Status |
|---|---|
| `u / uw` register | ✓ (previous draft had "je gegevens", "je locatie" — all changed) |
| H1 = John's natural contact-invite | ✓ `Neem gerust contact op` verbatim |
| John-signatures: `wat we voor uw bedrijf kunnen betekenen`, `voor, tijdens of na kantooruren`, `in overleg met u als klant`, `niet via een callcenter` | ✓ |
| No WhatsApp (per voice research — wrong channel for this segment) | ✓ |
| No "Versturen" button | ✓ |
| No em dashes in form subtext | ✓ (period used) |
| Phone format `06 23545276` | ✓ |
| Postcode format `XXXX XX` | ✓ placeholder |
| Email lowercased | ✓ |
| Trailing slashes | ✓ |
| KvK placeholder present, BTW deliberately omitted | ✓ |
| 7 service options in select (matches new diensten list) | ✓ |

**Total prose word count**: ~130 words (conversion page — intentionally minimal)
