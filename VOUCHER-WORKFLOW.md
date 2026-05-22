# Voucher workflow — návod pro Renátu

Krok-po-kroku co dělat, když někdo koupí dárkový poukaz přes web.

## Jak to celé funguje

```
Klient na webu → klikne "Koupit 3 000 Kč"
       ↓
Stripe checkout (Stripe vybere kartu, vezme peníze)
       ↓
Stripe pošle Renátě e-mail "New payment €120 EUR" + jméno klienta
       ↓
Renáta otevře voucher-pdf.html v prohlížeči
       ↓
Vyplní 4 pole (jméno obdarovaného, dárce, vzkaz, platnost)
       ↓
Cmd + P → "Save as PDF"
       ↓
Pošle PDF e-mailem klientovi
```

Celá akce: **3–5 minut**.

## Jednorázový setup (uděláš jen jednou)

### 1. Účet Stripe

1. Jdi na <https://stripe.com> → **Start now** → registrace
2. Doklady: IČO, bankovní účet, doklad totožnosti — Stripe pošle peníze na účet do 7 dnů od první platby
3. Po aktivaci jdi do **Dashboard → Products → Add product**

### 2. Vytvoř 3 produkty (3 částky)

Pro každou částku zvlášť:

**Produkt 1 — 1 500 Kč**
- Name: `Dárkový poukaz 1 500 Kč`
- Description: `Poukaz na masáž v Harmonie doteků, Jihlava. Platnost 12 měsíců.`
- Image: nahraj `og.jpg` z repa
- Price: `1500 CZK` jednorázová platba
- **Save → Klikni na produkt → Pricing → "Create payment link"**
- Zkopíruj URL co vznikne (vypadá jako `https://buy.stripe.com/abc123...`)

**Opakuj pro 3 000 Kč a 5 000 Kč.**

### 3. Vlož 3 linky do `voucher.html`

V repu otevři `voucher.html`, najdi tři placeholder URL:

```html
https://buy.stripe.com/REPLACE_LINK_1500
https://buy.stripe.com/REPLACE_LINK_3000
https://buy.stripe.com/REPLACE_LINK_5000
```

Nahraď je svými skutečnými linky ze Stripe. Commit + push → Vercel auto-deploy během minuty.

### 4. Stripe nastavení (volitelně, doporučeno)

V **Dashboard → Settings → Customer emails**:
- ✅ Successful payments (klient dostane potvrzení o platbě)
- ✅ Refunds (pro případ vrácení peněz)

V **Dashboard → Settings → Branding**:
- Logo: nahraj `favicon.svg` nebo `apple-touch-icon.png`
- Brand color: `#C9A36A`
- Tak Stripe checkout vypadá jako tvůj web.

## Provoz — co děláš při každé objednávce

### Krok 1: Notifikace ze Stripe

Stripe ti pošle e-mail s předmětem `You received a payment of 3000.00 CZK`. V něm:
- Jméno klienta
- E-mail klienta
- Datum
- Částka
- Reference (číslo platby)

### Krok 2: Otevři voucher template

Otevři <https://harmonie-doteku.cz/voucher-pdf.html> (klidně si ho ulož do záložek)

Stránka vypadá jako hotový poukaz se žlutě podtrženými políčky.

### Krok 3: Vyplň 4 pole

Klikni na žluté pole a přepíš:

1. **Č. HD-2026-001** — postupné číslování (HD-2026-002, HD-2026-003 …)
2. **Vystaveno** — dnešní datum
3. **3 000** — částka co klient zaplatil
4. **Pro** — jméno obdarovaného (pokud neuvedl, napiš "Pro Tebe" nebo nech volné)
5. **Od** — jméno klienta (ze Stripe notifikace)
6. **Vzkaz** — buď nech default, nebo si vymyslíš krátký osobní (klient může poslat v poznámce při platbě)
7. **Platnost do** — dnešní datum + 12 měsíců (např. zaplaceno 22. 5. 2026 → platnost do 22. 5. 2027)

### Krok 4: Uložit jako PDF

- **Mac:** `Cmd + P` → v dialogu klik na **PDF** dole vlevo → **Save as PDF**
- **Windows:** `Ctrl + P` → printer "Microsoft Print to PDF" → Save

Soubor pojmenuj `Harmonie-doteku-poukaz-HD-2026-001.pdf` (číslo z kroku 1).

### Krok 5: Pošli klientovi

E-mail klientovi (kterého máš ze Stripe notifikace):

> **Předmět:** Dárkový poukaz Harmonie doteků
>
> Dobrý den,
>
> děkuji za nákup dárkového poukazu. V příloze najdete PDF — můžete vytisknout nebo přeposlat dál.
>
> Poukaz má platnost 12 měsíců a vztahuje se na jakoukoliv masáž. Obdarovaný se může objednat na čísle +420 725 433 655 nebo e-mailem.
>
> Krásné dárkování!
>
> Renáta Altová
> Harmonie doteků · Matky Boží 1205/2, Jihlava

### Krok 6: Zapiš do evidence

Veď si jednoduchou tabulku (Excel, Apple Numbers, papír — co chceš):

| Č. poukazu | Datum vystavení | Klient | Částka | Platnost | Vyčerpáno? |
|---|---|---|---|---|---|
| HD-2026-001 | 22. 5. 2026 | Jana Nováková | 3 000 Kč | 22. 5. 2027 | ne |

Když přijde obdarovaný s číslem poukazu, zkontroluj v tabulce:
- Existuje?
- Není přečerpaný?
- Není po platnosti?

Pokud ano → masáž zdarma do hodnoty poukazu. Pokud poukaz pokrývá víc než masáž (např. poukaz 3000, masáž 1500), klient si může vybrat kombinaci nebo dolatit hotově.

Po vyčerpání → označit v tabulce.

## Drobnosti k vyladění (jednou udělat)

### Vlastní e-mail šablona

Můžeš si v Mail aplikaci (nebo Gmailu) uložit šablonu — ušetří tě psát stejný text:

- **Mail.app (Mac):** Soubor → Nový z šablony → vytvoř jednu
- **Gmail:** Settings → Templates → vytvoř

### Brandované Stripe potvrzení

V Stripe Dashboard → Settings → Branding nastav:
- Public name: `Harmonie doteků`
- Support email: `harmoniedoteku.masaze@gmail.com`
- Statement descriptor: `HARMONIE DOTEKU` (16 znaků max, na výpisu z karty)

### Vlastní částka

Klient napíše/zavolá. Vytvoříš **ad-hoc Stripe Payment Link**: Dashboard → Payments → Create payment → částka → kopíruj link → pošleš mu e-mailem.

## Statistiky

Stripe ti v Dashboardu ukáže:
- Tržby za měsíc / rok
- Kolik poukazů (= počet plateb)
- Průměrná hodnota
- Konverzní funnel (kolik lidí na webu kliklo, kolik dokončilo)

Pro daňové účely Stripe automaticky generuje měsíční report co stačí přeposlat účetnímu.

## Když něco nefunguje

| Problém | Řešení |
|---|---|
| Klient platil ale Stripe e-mail nepřišel | Zkontroluj spam, jinak Dashboard → Payments — uvidíš tam vše |
| Klient chce vrátit peníze | Dashboard → najdi platbu → **Refund** (Stripe pošle peníze zpátky během 5–10 dnů) |
| Platba selhala | Klientovi pošli novej Payment Link z Dashboardu |
| Nepamatuju si jak vytvořit PDF | Otevři `voucher-pdf.html`, klik na žluté pole, vyplň, `Cmd + P`, **PDF** dole vlevo |
| Chci změnit vzhled poukazu | Napiš Lukášovi, upraví HTML šablonu |

---

**Otázky?** Napiš Lukášovi, nebo zkus googlit "stripe payment link" — jsou tisíce tutoriálů.

První poukaz spolu projdeme krok po kroku.
