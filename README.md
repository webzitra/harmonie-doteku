# Harmonie doteků

Statický web pro **Renátu Altovou** — masérka v klenutém prostoru centra Jihlavy.

- **Lokace:** Matky Boží 1205/2, 586 01 Jihlava
- **Kontakt:** +420 725 433 655 · harmoniedoteku.masaze@gmail.com
- **Hodnocení:** 4,8 ★ z 9 recenzí (Firmy.cz)

## Stack

Pure static HTML/CSS/JS — žádný build step, žádné dependencies, jen native browser + Google Fonts CDN.

```
.
├── index.html        # hlavní stránka (10 sekcí)
├── tantra.html       # diskrétní subpage pro tantrické masáže
├── og.html           # OG image template (render → og.jpg)
├── og-tantra.html    # OG image pro /tantra
├── favicon.svg       # klenba s plamenem
├── og.jpg            # 1200×630 social share
├── og-tantra.jpg
├── sitemap.xml
├── robots.txt
├── fotky/            # 16 optimalizovaných fotek (max 1920w)
├── mood-board.md     # brand reference
└── wireframe.md      # section structure
```

## Lokální preview

```bash
python3 -m http.server 8092
open http://localhost:8092/
```

## Brand DNA

Sacred cave / svatyně, ne wellness spa. Klenba + dřevo + candle gold + Ganesha. Profi terapeutka, spirituální ale ne new-age.

- **Paleta:** cave `#0F0B08` · candle `#C9A36A` · terracotta `#A9603F` · linen `#E8DDC9`
- **Typo:** Cormorant Garamond display + Inter body + Cardo italic accents
- **Rytmus:** dark hero → cream intro → dark gallery → /tantra subroute

## Vytvořilo

[WebZítra studio](https://webzitra.cz) — design + code

Studio fotky: DCP Production
