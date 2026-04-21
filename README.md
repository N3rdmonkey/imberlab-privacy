# ImberLab Website v8

**Major upgrade vs v6/v7:**

- **SEO**: separate `/en/` and `/de/` URLs (not bilingual mash-up), proper hreflang tags, schema.org JSON-LD, Open Graph + Twitter cards, sitemap.xml, robots.txt
- **Design**: new "Lab Editorial" aesthetic — Fraunces serif display, JetBrains Mono accents, dark navy hero with lime power-color
- **Conversion**: hero with concrete value-prop in 2 seconds, use-case section for direct identification, single-card pricing
- **Content**: 8 SEO-keyword-rich features, 3 use-cases, 8 FAQ entries optimized for long-tail searches
- **Technical**: zero JS dependencies (one tiny vanilla snippet for FAQ), uses Google Fonts only, fully responsive mobile-first, accessible (semantic HTML, prefers-reduced-motion respected)

---

## File Structure

```
/index.html          → Auto-redirect to /en/ or /de/ based on browser language
/en/index.html       → English homepage
/en/privacy.html     → English privacy policy
/de/index.html       → German homepage  
/de/privacy.html     → German privacy policy
/css/style.css       → Single shared stylesheet
/screenshots/        → ⚠️ MUST be copied from old /screenshots folder
/sitemap.xml         → Submit to Google Search Console
/robots.txt          → Crawler instructions
/.nojekyll           → Disables GitHub Pages Jekyll processing
```

---

## Deployment to GitHub Pages

### Step 1 — Copy screenshots
The new website references `../screenshots/01_main_menu.png` etc.
**Copy your existing `/screenshots/` folder into the project root.**

### Step 2 — Push to your repo
```bash
git add .
git commit -m "v8: SEO + design overhaul with EN/DE separation"
git push
```

### Step 3 — Verify URL paths
The current sitemap and canonical tags reference  
`https://n3rdmonkey.github.io/imberlab-privacy/`

If you rename the repo (recommended → see Step 4), find/replace this URL  
in `sitemap.xml`, `index.html` files, and `robots.txt`.

### Step 4 — RECOMMENDED: Rename repo
The path `/imberlab-privacy/` looks like a "privacy page only" to Google.  
Rename to `imberlab` or `imberlab-app` — it instantly improves ranking.

GitHub: Settings → Repository name → rename → URL becomes  
`https://n3rdmonkey.github.io/imberlab/`

### Step 5 — Submit sitemap to Google
1. Go to Google Search Console → Add property → Add `https://n3rdmonkey.github.io/imberlab-privacy/`
2. Verify ownership (HTML file or DNS — DNS preferred if you use a custom domain)
3. Submit `sitemap.xml`
4. Wait 24-48h, watch impressions in the Performance tab

---

## Optional but recommended next steps

### Get a custom domain (~10€/year)
- `imberlab.app` (~12€/year) — best for tech app
- `imberlab.at` (~8€/year) — Austrian focus
- `imberlab.eu` (~5€/year) — EU focus
Map to `n3rdmonkey.github.io/imberlab/` via CNAME file in repo root.

### Add a blog section for SEO
Create `/blog/` with posts on long-tail keywords:
- "How to calibrate a pipette per EN ISO 8655 — step by step"
- "Levey-Jennings control chart explained"
- "GHS pictograms — a printable cheat sheet"
- "Pipette calibration: when DIY is enough vs. when you need accreditation"
Each post = 1500+ words = ranking opportunity.

### Open Graph image
Currently uses `01_main_menu.png` as OG image.  
Better: create a dedicated 1200x630px OG image with text overlay  
("ImberLab — Lab QC App") for richer social sharing previews.

---

## Design tokens (for future tweaking)

```css
--paper:    #FAF8F3   /* Off-white background */
--ink:      #0F1E2E   /* Deep navy text */
--lime:     #A3E635   /* Power accent */
--navy-deep:#0A1622   /* Hero background */
--line:     #E0DACA   /* Subtle borders */
```

Fonts: **Fraunces** (display serif), **Inter Tight** (body), **JetBrains Mono** (data)  
Loaded from Google Fonts — no local install needed.

---

## Testing checklist before going live

- [ ] All screenshots load (check `/screenshots/01_main_menu.png` etc.)
- [ ] EN/DE language switcher works on every page
- [ ] FAQ accordions expand/collapse
- [ ] Privacy policy address is correct (currently: Schulterbergstr. 4, 4742 Pram)
- [ ] Google Play link opens correctly: `play.google.com/store/apps/details?id=com.imber.labor`
- [ ] Mobile view: nav collapses, hero phone scales, no horizontal scroll
- [ ] Lighthouse score > 95 (Performance, SEO, Accessibility)

---

© 2026 Christoph Imber
