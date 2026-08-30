# EM Handover Daily — Birmingham Heartlands Hospital ED

A site-specific fork of [em-handover-daily](https://github.com/shakeymedic/em-handover-daily) for the BHH Emergency Department.

The Night Handover prompt follows the **BHH ED Handover Structure (Version 2, April 2026)** exactly:

| Section | Content |
|---|---|
| 1 | Introductions (cons + senior regs), attendance register, role allocation, thanks to finishing team, imminent blue lights, ABCDE (deaths, absconding, bed/specialty issues, equipment, safety alerts) |
| 2 | Resus handover · 5-min education/RCEM safety flash · Paediatric handover |
| 3 | Majors split from EDAA (separate in EDAA Drs office) |

---

## What's different from the generic repo

- `night-handover.html` — restructured to match the BHH 9-fieldset layout (Sections 1–3 above)
- `about.html` — references BHH ED and the handover structure version
- `data/modules.json` — same 12 seed modules; add BHH-specific content here
- Everything else is identical to the generic repo

---

## Keeping in sync with the generic repo

```bash
# Add the generic repo as an upstream remote
git remote add upstream https://github.com/shakeymedic/em-handover-daily.git

# Pull new modules, assets, and bug fixes (but not night-handover.html or about.html)
git fetch upstream
git checkout upstream/main -- assets/ data/papers.json data/rcem-alerts.json sw.js
git commit -m "Sync assets from upstream"
```

Changes to `night-handover.html` and `about.html` are intentionally BHH-specific — do not overwrite these from upstream.

---

## Deploying to Netlify

Same steps as the generic repo:

1. Push to GitHub
2. Netlify > Add new site > Import > this repo
3. Build command: *(blank)*
4. Publish directory: `.`
5. Deploy

---

## Adding BHH-specific content

### Teaching modules

Add to `data/modules.json`. Use `csv_to_modules.py` for bulk imports. All new modules start as `status: draft`.

Consider adding modules tagged to BHH local protocols or the RCEM safety flashes used at morning handover.

### Safety alerts

Add RCEM or trust-specific alerts to `data/rcem-alerts.json`. Entries older than 90 days are filtered automatically.

---

## Disclaimer

Educational resource only. Not a substitute for clinical judgement. Always refer to local guidelines and current BNF/NICE guidance.

Content created by Jake Turner. Curated with the assistance of AI (Perplexity). All content editorially reviewed.
