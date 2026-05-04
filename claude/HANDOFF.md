# JESIWICKS.COM — Claude Desktop Handoff Document
## Complete project context for executing changes directly via GitHub

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
- Freepik affiliate link must always be: `referral.freepik.com/mQQWXkD`
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
- Freepik affiliate: `referral.freepik.com/mQQWXkD`

---

## DEPLOYMENT PROCESS
1. Claude Desktop edits files and commits directly to `jesiwicks/jesiwicks.com` main branch
2. Cloudflare watches the GitHub repo and deploys automatically on every push
3. No manual steps needed after Claude Desktop commits

**NEVER delete a file and re-upload** — always use create_or_update_file which updates in place. Deleting causes 4xx errors in analytics during the gap between deletion and re-upload.

---

## FOOTER SERIES ROW
Every guide has a footer with links to the other guides. Current state:
- jesiwicks.com (home) — always active
- jesiwicks.com/seedance — active link
- jesiwicks.com/kling — active link
- jesiwicks.com/veo3 — active link
- Runway Gen-4.5 — coming soon (no link yet)
- Wan 2.6 — coming soon (no link yet)

When a new guide goes live, update the footer series row in ALL existing guide files.

---

## CLOUDFLARE ANALYTICS ISSUE (pending fix)
**Problem:** Cache rate is only 7%. Cloudflare analytics shows 37k+ requests returning "empty" content type. This means Cloudflare is not caching HTML files properly.

**What needs to happen:** Read the `wrangler.toml` file in the repo, then add proper cache headers so Cloudflare caches HTML, fonts, and images at the edge. This will fix the 7% cache rate and reduce load times for international visitors.

**Important:** Do NOT delete any files. Do NOT change any guide content. Only modify `wrangler.toml` or add a cache configuration. Show the proposed change before committing.

---

## CURRENT SITE PERFORMANCE (April 19, 2026)
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
1. **Fix Cloudflare caching** — read wrangler.toml, add cache headers, commit
2. **Enable Cloudflare Web Analytics** — adds page-level traffic data, currently only site-level analytics exist
3. **Next guide** — Grok Imagine is the highest priority based on search interest and creator community activity

---

## SESSION HISTORY (condensed from full transcripts)

### Session 1 — April 13, 2026
Initial build of Seedance 2.0 guide. Established JESIWICKS brand, mobile responsiveness, and planned the multi-model guide series at jesiwicks.com.

### Session 2 — April 14, 2026 (morning)
Seedance guide redesign — Version B Jesiwicks brand. Design mockup iteration, accessibility audit, color system refinement, instructional design framework.

### Session 3 — April 14, 2026 (mid-morning)
Full Seedance 2.0 guide build — design system refinement, accessibility audit, research findings, content accuracy audit. Floating cheat sheet added.

### Session 4 — April 14, 2026 (afternoon)
Design fixes, content accuracy audits, mobile optimisation, performance audit, accessibility/SEO fixes, How It Thinks and Your Toolkit tab content editing. Platform table rebuilt.

### Session 5 — April 14, 2026 (evening)
Nav responsiveness fixes, mobile card layout for tables, pricing table updates, content accuracy audits, platform table rebuilds, sources page updates.

### Session 6 — April 14, 2026 (night)
Seedance guide finalization, SEO optimization, accessibility, performance, GitHub deployment, homepage updates, OG image creation.

### Session 7 — April 15, 2026 (afternoon)
Full site launch — Seedance guide finalization, GitHub deployment, Cloudflare migration from Netlify, DNS configuration, PageSpeed optimization, SEO fixes, social card validation, FAQ research.

### Session 8 — April 15, 2026 (evening)
Kling 3.0 guide started using Seedance as template. Research-first approach, SEO strategy, file structure with placeholders, headline decisions.

### Session 9 — April 15, 2026 (evening continued)
Kling guide continued — systematic research, CSS debugging, layout fixes, platform table audit, content development.

### Session 10 — April 15, 2026 (night)
CSS architecture fixes, design system alignment with Seedance guide, section redesigns — Core Technique, Character Consistency, Motion Control, Toolkit. Pricing table audit and verification.

### Session 11 — April 15, 2026 (late night)
How It Thinks redesigns — Core Technique formula grid + annotated prompt, Character Consistency redesign. Toolkit redesigns — pricing table, platform table, gotcha list. Playbook tab, Reality Check tab built.

### Session 12 — April 15-16, 2026 (overnight)
Playbook tab (3 levels with copy-paste templates), Reality Check tab (5 mistakes, hard limits, credit conservation, when to switch, checklist), FAQ tab (10 questions + bonus), Sources tab (30 sources across 3 tiers), footer fixes.

### Session 13 — April 16, 2026
Kling guide completion — FAQ tab, Sources tab update, SEO audit, code cleanup, OG image creation, GitHub deployment, Cloudflare routing fixes, div balance debugging.

### Session 14 — April 17, 2026
Major refinement session — SEO audits, code quality audits, Kling and Veo 3 deployment, CSS fixes, headline rewrites, clarity audits, accessibility fixes, GitHub branch protection, README creation, sitemap updates, AI video model priority research.

### Session 15 — April 19, 2026
- Visual redesigns: @ Tag System and Why Characters Drift sections in Seedance guide rebuilt with card-based layouts
- Watermark fixes across all guides
- Level 3 Playbook rebuilt in consistent design language
- Dark mode purple updated to #B87FEE in both Seedance and Kling
- Clarity audits on both Seedance and Kling
- Kling headlines: all 19 rewritten with proper grammar, periods inside gradient tags, no forced br breaks
- Veo 3 deployed: sitemap updated, homepage card activated, footer links in Seedance and Kling made live
- Cloudflare analytics: 45 countries, 26% 4xx rate (trending down), 7% cache rate (needs fixing)
- Full deployment infrastructure set up: Claude Code, GitHub CLI, Claude GitHub App, GitHub Desktop, Claude Desktop with GitHub MCP via Docker