# BootFit

**Know exactly what size football boots to buy.**

BootFit tells you what size to buy in your next pair of football boots, based on a boot you already own (or your foot measurements), official brand size charts, and reviewer-researched fit data. Every recommendation comes with a confidence tier, the evidence behind it, and a plain explanation of the reasoning. It never pretends to be more certain than the data allows.

## Live site

The entire product is a single file: `index.html`. Host it anywhere static:

- **Vercel**: import this repo at vercel.com/new, no config needed
- **Netlify**: drag the repo folder into app.netlify.com/drop
- **GitHub Pages**: repo Settings, Pages, deploy from the main branch root

## What it does

- **Landing page (Home)** with a live boot-to-boot demo powered by the real engine
- **Find Size**: Engine A (reference boot, most accurate) and Engine B (foot profile: measurements, everyday sneaker cross-check, experience questions)
- **Compare**: up to 3 target boots against your foot profile
- **My Boots**: your foot profile, recommendation history, and fit reports
- **Data**: the full boot database with per-model confidence labels and sources

Recommendations separate objective facts (size charts, reviewer consensus) from BootFit's prediction, show a size ladder (how sure we are about each nearby size), warn when a width mismatch cannot be fixed by sizing up, and go conservative when evidence is thin.

## Data honesty

The seed database covers 16 current elite-tier boots across Nike, Adidas, Puma, Mizuno, and New Balance. Fit characteristics were researched from linked public reviewer sources and official size charts (July 2026), and every boot carries a data-confidence label. There are no fabricated player-report counts: the community evidence line reads zero until real reports exist.

## Source layout

```
index.html                 the complete built site (landing + app, one file)
src/engine.js              boot database, size charts, recommendation engine
src/app.js                 app UI logic
src/index.template.html    app page template
src/landing.template.html  landing page template
src/build_combined.py      builds index.html from the templates + engine + app
src/test.js                43 engine tests (node src/test.js)
src/smoke*.js              Playwright browser walkthroughs
```

To rebuild after editing the source: run `python3 build_combined.py` inside `src/` with the templates and JS files beside it, then move the output.

## Roadmap

The prototype keeps all state in memory by design. The production path is Next.js + Supabase: persistent accounts, verified community fit reports with weighted evidence, and an admin dashboard for the boot database.

## Disclaimer

BootFit is an independent tool, not affiliated with or endorsed by Nike, Adidas, Puma, Mizuno, or New Balance. Sizing is guidance, not a guarantee.
