# Harmonie doteků — Wireframe

> Section-by-section structure pro hlavní stránku a tantra podstránku.
> Každá sekce má: cíl · obsah · foto · poznámka k chování.

---

## Navigation (sticky, transparent → solid on scroll)

```
[ HARMONIE DOTEKŮ ]              Prostor   Masáže   Tantra   O mně   Kontakt   [ Rezervovat ]
```

- Logo = wordmark v Cormorant Garamond 400, letter-spacing 0.08em
- Linky Inter 500, uppercase, tracking, 12px
- CTA „Rezervovat" candle gold button, malé, ne agresivní
- Mobile: hamburger → fullscreen overlay s linky velkými serify

---

## Home (`/`)

### 1. HERO — „Místo, kde se dotek stává řečí"
**Cíl:** Lapnout dech. Komunikovat jedinečnost prostoru za 3 sekundy.

- Full-bleed foto **#1** (klenutá místnost s futonem) s tmavým gradient overlay (0.55 opacity zleva, 0.3 dole)
- H1 velký serif, 2 řádky, jedno slovo v italice
- Pod tím podtitul Inter 17px max-width 380px
- 2 CTA: primary „Rezervovat čas" (candle gold), secondary „Projít prostorem" (text link s šipkou)
- Subtle scroll-cue dole (▼ + slovo „dál")
- **Animace:** image ken-burns velmi pomalu (8s), text fade-in po 200ms, podtitul po 400ms

### 2. EYEBROW STRIP — minimální fakta
**Cíl:** Důvěra za 2 sekundy.

```
Klenutý prostor · centrum Jihlavy · 7 typů masáží · 4,8 ★ z 9 recenzí · od roku XXXX
```
Centrovaný řádek Inter 400, 13px, candle gold separátory.

### 3. INTRO — krátký kvazi-manifest
**Cíl:** Říct co se tady děje slovem, ne výčtem.

- 2 sloupce desktop, stack mobile
- Levý: foto **#10** (Ganesha + svíčky detail) — vysoký poměr 3:4
- Pravý: krátký text, 80–120 slov, end-rhyme do CTA „Poznejte mě →"
- Background: Sand (`#F4ECDD`)

### 4. PROSTOR (gallery sekce)
**Cíl:** Ukázat že tohle není standardní studio.

- Eyebrow: „Prostor"
- H2: „Klenba, dřevo, světlo"
- Krátký lead, 1 odstavec
- **Masonry grid** 3 sloupce desktop, 2 mobile, fotek 5–7 (1, 2, 4, 8, 13, 7)
- Subtle hover: scale 1.02 + caption fade-in (jedno slovo: „Hlavní místnost" / „Vstup" / „Detail")
- Background: Cave (`#0F0B08`) — fotky září

### 5. MASÁŽE — služby grid (bez tantry)
**Cíl:** Konkrétní výběr, ale ne ceník.

- Eyebrow: „Masáže"
- H2: „Vyberte si druh dotyku"
- 6 karet (3×2 desktop, 1× stack mobile):
  - **Sportovní** — 90 / 150 min — od 1 000 Kč
  - **Relaxační** — 90 / 150 / 180 min — od 1 200 Kč
  - **Lymfatická** — 60 / 90 / 120 min — od 600 Kč
  - **Maderoterapie** — dle dohody
  - **Energetická** — 30 / 90 min — od 500 Kč
  - **Kundalini Awakening** — 90 min — 2 000 Kč
- Karta: tmavý card, eyebrow + H3 serif + krátký popis 2 řádky + cena/délka + „Více →"
- Klik → otevře sliding panel sprava (ne nová stránka) s plným popisem a všemi cenami
- 7. „karta" / poslední pozice: **Tantra** = jiný styling (terracotta border), „Vlastní cesta →" vede na `/tantra`

### 6. RENATA — about block
**Cíl:** Personifikace. Lidský obličej za prostorem.

- 2 sloupce — left foto (portrét; pokud chybí, dotočit), right text
- H2: „Renata Altová"
- Eyebrow: „Masérka a facilitátorka"
- Text: 150–200 slov, krátké odstavce
  - kdo je, jak začala, co studuje/cvičí
  - certifikace (potřebujeme dotahnout — momentálně chybí, zeptat se)
  - filozofie 1 větou
- Tlačítko „Číst dál" → /o-mne (extended bio)
- Background: Linen (`#E8DDC9`), text Bark

### 7. RITUÁL — co se stane když přijdete
**Cíl:** Snížit anxiety prvního klienta.

- Tmavá sekce (Cave)
- H2: „Jak vypadá hodina u mě"
- 4 kroky horizontálně (mobile vertikálně):
  1. **Krátký hovor** — zjistíme co tělo potřebuje
  2. **Vědomý vstup** — pomalé naladění, dech
  3. **Doteky** — sám/sama si určujete tempo
  4. **Doznění** — čaj, ticho, návrat
- Číslo velký serif v candle gold, krátký text Inter
- Žádné ikony — typografie nese

### 8. RECENZE
**Cíl:** Social proof bez křiku.

- Eyebrow: „Z recenzí"
- 3 citáty editorial style — velký serif italic citation, autor jméno + zdroj (Firmy.cz / Google) malý
- Možno carousel ručně přepínatelný, ale **bez auto-rotate**
- Link „Všechny recenze na Firmy.cz →"

### 9. LOKACE
**Cíl:** Najít cestu.

- 2 sloupce: vlevo foto **#16** (náměstí) nebo **#13** (vchod), vpravo adresa + jak se dostat
- Embedded mapa **až po klikutí** (privacy + perf) — placeholder s „Otevřít mapu"
- Text: „Matky Boží 1205/2 · Jihlava · vstup pod loubím vedle XXX"
- Doprava: pěšky 5 min z autobusového nádraží, parkování (vyřešit info)

### 10. KONTAKT + REZERVACE
**Cíl:** Domluvit termín bez tření.

- H2: „Rezervovat čas"
- Telefon velký click-to-call, email, WhatsApp
- Krátký formulář (jméno, telefon, typ masáže select, preferovaný den, zpráva) — POST na klient inbox
- Otevírací hodiny tabulkou Po–Ne 8:00–20:00
- Subtle „Odpovídám obvykle do 4 hodin"

### 11. FOOTER
- 3 sloupce: contact / quick links / social
- Mosazný (candle) wordmark
- IČO, copyright, „Web vytvořila WebZítra studio"
- Cookie banner = minimal, dole levo

---

## /tantra (subroute)

### 1. HERO TANTRA — tlumenější, intimnější
- Foto **#8** nebo **#2** (klenutá místnost s mech panelem)
- H1: „Tantra je řeč těla, ne technika." (nebo: „Vědomá cesta k vlastní hloubce.")
- Bez čísel, bez ceny, bez CTA → scroll cue dolů

### 2. CO TO JE / CO TO NENÍ
**Cíl:** Otevřeně demystifikovat, oddělit od erotic massage konkurence.

- 2 sloupce: „Tantra u mě **je**" / „Tantra u mě **není**"
- 4 body každý — krátké tvrzení Inter 16px
- Background: Sand

### 3. PRO KOHO
- Eyebrow + H2: „Pro koho je tantra"
- 3 cesty:
  - **Muž** — 90 / 120 / 150 / 180 min · 3 500 – 5 900 Kč
  - **Žena** — 90 / 120 / 150 / 180 min · 3 000 – 5 400 Kč
  - **Pár** — 90 / 120 / 150 / 180 min · 6 000 – 10 800 Kč
- Plus „Pár — transformace 240 min · 10 500 Kč"
- Karty stylové, ne ceník

### 4. RITUÁL TANTRY — etika a hranice
**Cíl:** Trust + safety.

- Krátký text, jasné věty:
  - Co se dělá / co se nedělá
  - Vědomý souhlas
  - Konzultace předem
  - Co očekávat fyzicky
- Background: Ember (`#1E1410`), text Linen

### 5. KUNDALINI AWAKENING (facilitátorka)
- Krátká sekce s vlastní hierarchií
- Vysvětlit terminologii
- Cena 2 000 Kč / 90 min

### 6. CITACE / DEDIKACE
- 1 editorial citace italic, autor (např. Osho, Margot Anand) — Renata vybere

### 7. REZERVACE — odlišná
- Bez quick-formuláře. „Tantrický termín se domlouvá po krátkém telefonickém rozhovoru."
- Telefon, email, WhatsApp
- Jemný gentle CTA

### 8. FOOTER (shared)

---

## Mobile considerations

- Hero H1 clamp(40px, 9vw, 64px) — nesmí přetékat
- Galerie 2 sloupce, ne 3
- Karty služeb full width, swipe nemá smysl — stack
- Sticky CTA „Rezervovat" dole jen na služby/tantra stránkách, ne hp (nebýt agresivní)
- Mapa = jen tlačítko otevři v Mapy.cz nativně

---

## Drobné rules

- **No carousel auto-play.** Nikde.
- **No modal popups.** Ani newsletter.
- **No emoji.**
- **Image lazy loading + width/height** atributy povinné (CLS = 0).
- **Reduced motion respect** — všechny animace off pod `prefers-reduced-motion`.
- **Czech first**, EN/DE variant later (nepoužívat machine překlad — když, tak ručně).
