# ImberLab Website v8 — Ready to Deploy

Alles ist drin. Nur noch ins Repo kopieren und pushen.

---

## 🚀 Deploy (3 Schritte)

### 1. Backup vom aktuellen Repo (Sicherheit)
```bash
cd path/to/imberlab-privacy
git checkout -b v7-backup  # aktuellen Stand als Branch sichern
git checkout main
```

### 2. Alles aus diesem ZIP ins Repo-Root kopieren
Entpacke das ZIP. Kopiere **alles** aus `ImberLab_Website_v8/` direkt ins **Root** von `imberlab-privacy`, **überschreibe** vorhandene Dateien.

Danach sollte die Struktur so aussehen:
```
imberlab-privacy/
├── index.html          (NEU — leitet automatisch auf /en/ oder /de/ weiter)
├── .nojekyll           (NEU — deaktiviert Jekyll)
├── robots.txt          (NEU)
├── sitemap.xml         (NEU)
├── css/style.css       (NEU)
├── en/index.html       (NEU)
├── en/privacy.html     (NEU — Inhalt 1:1 aus v6)
├── de/index.html       (NEU)
├── de/privacy.html     (NEU — Inhalt 1:1 aus v6)
├── screenshots/        (6 Screenshots, schon drin)
└── README.md           (diese Datei)
```

Alte `index.html`, `privacy.html` oder andere `.md`/`.html`-Dateien aus v6/v7 in der Root kannst du löschen — werden nicht mehr referenziert.

### 3. Push
```bash
git add .
git commit -m "v8: SEO overhaul — EN/DE Trennung, schema.org, neues Design"
git push origin main
```

GitHub Pages baut in ~30 Sekunden neu. Dann aufrufen:
- https://n3rdmonkey.github.io/imberlab-privacy/ (Auto-Redirect nach Browsersprache)
- https://n3rdmonkey.github.io/imberlab-privacy/en/
- https://n3rdmonkey.github.io/imberlab-privacy/de/

---

## ✅ Nach dem Live-Gang

### Google Search Console (5 Min, kritisch fürs Ranking)
1. https://search.google.com/search-console öffnen
2. Property hinzufügen: `https://n3rdmonkey.github.io/imberlab-privacy/`
3. Verifizierung (gleicher Google-Account wie Repo → automatisch)
4. **Sitemaps** → eintragen: `sitemap.xml`
5. 24-48h warten → im Performance-Tab siehst du, welche Suchanfragen treffen

### Schnellere Indexierung
- Search Console → URL-Prüfung → `/en/` und `/de/` URL einfügen → **Indexierung beantragen**

---

## 🔧 Optional (später)

### Repo umbenennen: `imberlab-privacy` → `imberlab`
Google interpretiert `imberlab-privacy` als "das ist eine Privacy-Seite" — schlecht fürs Ranking der App-Seite.
- GitHub → Settings → Repository name → `imberlab`
- URL wird zu `n3rdmonkey.github.io/imberlab/`
- **WICHTIG:** Wenn du umbenennst, musst du `imberlab-privacy` durch `imberlab` ersetzen in:
  - `sitemap.xml`
  - `index.html` (root)
  - `en/index.html`, `de/index.html`
  - `en/privacy.html`, `de/privacy.html`
  - `robots.txt`

Sag Bescheid, dann bau ich ein zweites ZIP mit bereits aktualisierten URLs.

### Eigene Domain (~10 €/Jahr)
- `imberlab.app` — beste Wahl für Tech-App
- `imberlab.at` — Österreich-Fokus
- `imberlab.eu` — EU-Fokus
Eine `CNAME`-Datei mit der Domain ins Repo → GitHub übernimmt automatisch.

### Blog für Long-Tail SEO
`/blog/` mit Artikeln zu Nischen-Suchanfragen:
- "Pipette kalibrieren nach EN ISO 8655 — Schritt für Schritt"
- "Levey-Jennings-Regelkarte erklärt"
- "GHS-Piktogramme Spickzettel"
- "DIN 32645 Nachweisgrenze berechnen"

Jeder Artikel = neue Seite = neue Ranking-Chance.

---

## 🎨 Was ist neu in v8

### SEO-Fundament
- **Getrennte EN/DE URLs** (`/en/` und `/de/`) — war vorher zweisprachig im selben HTML-Element (Google-Killer)
- `hreflang`-Alternates auf jeder Seite
- `schema.org` JSON-LD für MobileApplication (ermöglicht Rich Snippets)
- Volles `<meta>`-Set: title, description, canonical, Open Graph, Twitter Cards
- `sitemap.xml` mit Sprach-Alternates
- `robots.txt`
- Keyword-optimierte H1s, H2s und Feature-Texte

### Design: "Lab Editorial"
- Fraunces Serif für Headlines (unverwechselbar, nicht generisch)
- JetBrains Mono für Daten-Akzente (Normen, Kennzahlen)
- Off-White Papier-Hintergrund (`#FAF8F3`)
- Tiefes Navy Hero (`#0F1E2E`) mit Lime-Power-Color (`#A3E635`)
- Hero mit floating Data-Cards (±0.6%, CV 0.42, Next due 28d)

### Content
- Hero: "Lab quality control, without the paperwork." / "Labor-Qualitätskontrolle, ohne den Papierkram."
- 9 Feature-Cards mit Lucide-artigen Icons
- 3 Use-Cases (QS-Techniker / Analyt. Chemiker / Laborleiter)
- 6-Screenshot-Grid
- Single-Card-Preis (12,99 € einmalig)
- 8 FAQ-Einträge inkl. Vergleichstabelle vs Papier/Excel
- Dunkler CTA-Footer

### Technisch
- Null JS-Abhängigkeiten (nur 6 Zeilen Vanilla-JS fürs FAQ-Akkordeon)
- Eine gemeinsame CSS-Datei (~980 Zeilen)
- Nur Google Fonts (Fraunces + Inter Tight + JetBrains Mono)
- Komplett responsive mobile-first
- `prefers-reduced-motion` respektiert
- Semantisches HTML, zugänglich

---

## Design-Tokens (für spätere Anpassungen)

```css
--paper:     #FAF8F3   /* Off-White Hintergrund */
--ink:       #0F1E2E   /* Dunkles Navy Text */
--lime:      #A3E635   /* Power-Akzent */
--navy-deep: #0A1622   /* Hero-Hintergrund */
--line:      #E0DACA   /* Dezente Rahmen */
```

---

## Testing-Checkliste

Bevor du was ankündigst: `index.html` lokal im Browser öffnen und durchklicken:
- [ ] Root leitet automatisch auf `/en/` oder `/de/` um (je nach Browsersprache)
- [ ] Sprachumschalter funktioniert auf jeder Seite
- [ ] FAQ-Akkordeons gehen auf/zu
- [ ] Alle 6 Screenshots laden im Showcase
- [ ] Hero-Phone-Bild lädt (Screenshot 02)
- [ ] Privacy: Adresse stimmt (Schulterbergstr. 4, 4742 Pram)
- [ ] Google Play-Link: `play.google.com/store/apps/details?id=com.imber.labor`
- [ ] Mobile (DevTools → Responsive 375px): Nav klappt ein, kein horizontales Scrollen
- [ ] Lighthouse: Performance, SEO, Accessibility alle > 95

---

© 2026 Christoph Imber · Pram, Österreich
