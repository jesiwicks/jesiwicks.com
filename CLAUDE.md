# JESIWICKS.COM — Claude Code Project Context
## Complete project context for executing changes locally and pushing to GitHub

---

## WHO YOU ARE WORKING WITH
**Jessica Wicks Kelly (Jesi)** — jesiwicks@gmail.com
**Brand:** JESIWICKS
**Site:** jesiwicks.com
**GitHub repo:** jesiwicks/jesiwicks.com (main branch)
**Stack:** Static HTML + CSS + vanilla JS, deployed via Cloudflare Workers, hosted on GitHub, domain via Namecheap

---

## WHAT THE SITE IS
A free AI video guide series. Each guide is a single self-contained HTML file covering one AI video model in depth — how it works, prompt templates, pricing, platform comparisons, honest limitations, sourced FAQs. Accuracy is the primary value. No claims go in without verification.

---

## LIVE GUIDES (April 2026)
| Guide | URL | File in repo |
|-------|-----|--------------|
| Seedance 2.0 | jesiwicks.com/seedance | /seedance/index.html |
| Kling 3.0 | jesiwicks.com/kling | /kling/index.html |
| Veo 3 | jesiwicks.com/veo3 | /veo3/index.html |

Coming soon: Grok Imagine, Runway Gen-4.5, Meta AI, Hailuo 02, Wan 2.6

---

## REPO STRUCTURE
```
jesiwicks/jesiwicks.com (main branch)
├── index.html              — homepage
├── sitemap.xml
├── _redirects              — Cloudflare routing rules
├── wrangler.toml           — Cloudflare Workers config
├── robots.txt
├── README.md
├── og-image.jpg            — root OG image
├── avatar.webp
├── googleebe86f480b7f6fce.html — Google Search Console verification
├── fonts/                  — self-hosted Montserrat WOFF2 files
├── seedance/
│   ├── index.html
│   └── og-image.jpg
├── kling/
│   ├── index.html
│   └── og-image.jpg
└── veo3/
    ├── index.html
    └── og-image.jpg
```

---

## ABSOLUTE RULES — APPLY TO EVERY FILE YOU TOUCH

### Writing/formatting
- **No em dashes (—)** anywhere in content — use hyphen (-) or rewrite
- **No periods at end of titles or headlines** UNLESS the period is inside a gradient span as part of design
- Periods that ARE part of gradient design go INSIDE the `<em>` or `<span class="grad">` closing tag

### HTML structure
- `<!DOCTYPE html>` at top of every file
- All buttons must have `type="button"`
- No `javascript:void(0)` hrefs — use `href="#sources"` with `onclick="return false"` on Research & Sources links
- No Google Fonts — all fonts self-hosted from `/fonts/`
- Magnific affiliate link must always be: `https://referral.magnific.com/mzQWXkD`
- Every file must have zero em dashes when complete

### Guide-specific rules
- `hero-model-bg` watermark text must ALWAYS show the model name (e.g. "Seedance 2.0", "Kling 3.0", "Veo 3") on EVERY tab — never the tab name or section title
- `.hero-h1 .grad` must always have `display:inline` (never block — block causes forced line breaks)
- `.mistake-fix` must have `line-height:1.7`
- `.info-box.box-tip` uses green not purple (accessibility contrast fix)
- Dark mode `--purple:#B87FEE` (not #9B5DE5)
- Dark mode rgba: `rgba(184,127,238,` (not `rgba(155,93,229,`)
- Light mode purple is different per guide — DO NOT change light mode purple
  - Seedance light mode: `--purple:#6B2FBE`
  - Kling light mode: `--purple:#5A22A8`

---

## GUIDE ANATOMY
Each guide is one HTML file with 7 tabs (pages):

| Tab name | Page ID |
|----------|---------|
| What It Is | page-orient |
| How It Thinks | page-think |
| Your Toolkit | page-toolkit |
| The Playbook | page-playbook |
| Reality Check | page-reality |
| FAQ | page-faq |
| Sources (hidden, footer link only) | page-sources |

Each page has:
- A hero section with `hero-h1` heading (uses `<span class="grad">` for gradient)
- `sec-h2` section headings (use `<em>` for gradient)
- Gradient periods go INSIDE the closing tag of `<em>` or `<span class="grad">`
- `hero-model-bg` watermark in every page showing model name
- A footer with the series navigation row

---

## SEO REQUIREMENTS — EVERY GUIDE FILE
- Schema `@graph` with both `Article` AND `FAQPage`
- Full OG block: `og:site_name`, `og:image:width/height`, `og:locale`, all `article:` tags
- `| Jesiwicks` in the title tag
- `robots: index, follow`
- Keywords array in schema includes model-specific SEO terms
- Self-hosted fonts, no Google Fonts
- Magnific affiliate: `https://referral.magnific.com/mzQWXkD`

---

## DEPLOYMENT PROCESS
1. Edits are made locally via Claude Code in the working copy at `~/Desktop/jesiwicks.com`
2. Changes are committed with git and pushed to `jesiwicks/jesiwicks.com` main branch
3. Cloudflare watches the GitHub repo and deploys automatically on every push
4. No manual steps needed after the push completes

**NEVER delete a file and re-add it** — always edit in place. Deleting and re-creating causes 4xx errors in analytics during the gap between deletion and the next deploy, and creates noisier git history. Use Edit/Write on the existing path.

---

## FOOTER SERIES ROW
Every guide has a footer series row. Order matches what's in the HTML, top to bottom:
1. Seedance 2.0 — active link to `/seedance` (rendered as non-link pink span on the Seedance guide itself)
2. Kling 3.0 — active link to `/kling` (non-link pink span on the Kling guide)
3. Veo 3 — active link to `/veo3` (non-link pink span on the Veo 3 guide)
4. Grok Imagine — coming soon (no link)
5. Runway Gen-4.5 — coming soon (no link)

When a new guide goes live, update the footer series row in ALL existing guide files.

---

## CLOUDFLARE CACHING (resolved)
The April 19 baseline showed a 7% edge cache rate with HTML responses returning empty content type. Fix shipped May 4, 2026 in commit `ae67f2d`, which added a `_headers` file setting `CDN-Cache-Control: public, max-age=3600, stale-while-revalidate=86400` on `/*` plus long-lived immutable caching on `/fonts/*` and 30-day caching on image extensions.

Verified working May 19, 2026 via `curl -I https://jesiwicks.com/` and `curl -I https://jesiwicks.com/seedance/`: both responses returned `cf-cache-status: HIT` with `cdn-cache-control` present and matching the `_headers` declaration. Workers Static Assets is honoring `_headers` as expected.

---

## CURRENT SITE PERFORMANCE (April 19, 2026 — pre-caching-fix snapshot)
Caching figures below are from before the May 4 `_headers` fix. Edge cache rate has since been verified healthy (see Cloudflare Caching section). Other metrics may also be stale; re-check the Cloudflare dashboard for current numbers.

- 45 countries in first week of full deployment
- 41k requests, 881 visits, 1.22k page views
- 100% encrypted traffic (SSL)
- PageSpeed: 100 across all four categories on all three guides
- Rich Results: 2 valid items (Article + FAQPage) on all three guides
- Google Search Console: all three guides submitted and indexed
- 4xx error rate: 26% (trending down from 55% earlier in week — caused by deployment churn, not ongoing issue)

---

## BRAND VOICE
- Direct and honest — no hype, no marketing language
- Creator-to-creator tone
- "Here's what it actually does" not "revolutionary AI experience"
- Willing to publish honest negatives
- Accuracy over completeness — if unverifiable, leave it out

---

## THINGS TO NEVER DO
- Never change light mode purple values
- Never use em dashes
- Never use Google Fonts or any external font CDN
- Never delete files from GitHub — always update in place
- Never add periods to sec-label text
- Never change the `hero-model-bg` watermark to show a tab name
- Never use `display:block` on `.hero-h1 .grad`
- Never add `<br>` tags inside `hero-h1` or `sec-h2` elements
- Never reproduce the old rgba(155,93,229, values in dark mode

---

## PENDING TASKS
1. **Enable Cloudflare Web Analytics** — adds page-level traffic data, currently only site-level analytics exist
2. **Next guide** — Grok Imagine is the highest priority based on search interest and creator community activity
