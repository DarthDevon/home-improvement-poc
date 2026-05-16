# Howe Renovations POC — Project State

**Status:** SENT TO MIKE FOR REVIEW (2026-05-16). Awaiting feedback. Full site shipped: real logo + all 6 project case studies + hero carousel + form wired to `howerenovationsllc@gmail.com` + AEO/SEO foundation (LocalBusiness/FAQ/Breadcrumb schema, 3 area pages, 5 Q&A pages, sitemap.xml, robots.txt) + 4-column footer exposing the new pages + mobile-optimized (lazy images, visible phone CTA on sub-pages) + **Hydra chat widget installed on all 10 pages with knowledge source = the marketing site itself (19 chunks indexed)**. Mike's Hydra tenant fully set up (login email also corrected from a `gamil.com` typo in his original signup). Review checklist sent: `mike-review-checklist.txt`.
**Last updated:** 2026-05-16
**Last deploy:** Netlify `howe-renovations-preview.netlify.app` — deploy `6a08fb455d1014e174c6b9cc` (2026-05-16, Production READY, Hydra widget embed live across all pages).
**Site ID:** `3d292da9-cbe4-4f18-bce5-0b83360a54b9` (Netlify team `devonstreckfuss` / "Streck Ventures", Free tier).
**Hydra integration (tenant `howe-renovations-crw9`):** widget slug `howe-renovations-bd26c1` · color `#F9C787` salmon · bot "Support Bot" (`db5eb841-…`) · tracking + bot-visitor-context enabled · knowledge source `38f39669-…` crawls the Netlify preview URL with `crawl_all=true`.

---

## Client

| Field | Value |
|---|---|
| Business | Howe Renovations (aka Howe Home Improvement) |
| Owner | Mike |
| Location | **O'Fallon, Missouri** — works the St. Louis metro area. The previously-noted "Center Barnstead, NH" address and (603) 776-0611 phone were wrong (Buzzfile mismatch on a similarly-named "603 Coatings LLC" — different business entirely). Discarded as of 2026-05-16. |
| Phone | **636-697-2408** (636 = St. Louis / O'Fallon area code — pulled from howerenovations.com/home) |
| FB Page | `facebook.com/pages/category/Contractor/Howe-Home-Improvement-134086539948962/` |
| Existing site | `howerenovations.com` — Bookmark Connect builder template; HOME page has the real logo + tagline + phone (root URL returns the stock "WELCOME" view) |
| Real tagline on live site | "We build decks and other stuff!" — using as accent quote in the About section |
| Mike's stated tagline (per chat history) | "Make your house a home" — using as the primary hero headline |

---

## Live URLs

| Surface | URL |
|---|---|
| Preview (share with Mike) | https://howe-renovations-preview.netlify.app |
| Netlify admin | https://app.netlify.com/projects/howe-renovations-preview |
| Netlify Forms admin | https://app.netlify.com/projects/howe-renovations-preview/forms |
| GitHub repo | https://github.com/DarthDevon/home-improvement-poc (private) |
| Future custom domain | howerenovations.com (Mike's; point DNS at Netlify when ready) |
| Sitemap | https://howe-renovations-preview.netlify.app/sitemap.xml |
| robots.txt | https://howe-renovations-preview.netlify.app/robots.txt |

### All discoverable URLs (10)

| URL | Purpose |
|---|---|
| `/` | Home — hero, carousel, services, featured work, about, contact |
| `/gallery.html` | 6 project case studies (Mike's words) |
| `/areas/ofallon-mo/` | Local landing page — O'Fallon, MO |
| `/areas/st-charles-mo/` | Local landing page — St. Charles, MO |
| `/areas/st-peters-mo/` | Local landing page — St. Peters, MO |
| `/answers/composite-vs-wood-deck-cost-and-lifespan/` | AEO Q&A |
| `/answers/how-long-does-a-bathroom-remodel-take/` | AEO Q&A |
| `/answers/how-to-tell-if-deck-or-subfloor-is-rotted/` | AEO Q&A |
| `/answers/when-to-repair-vs-replace-old-deck/` | AEO Q&A |
| `/answers/can-you-remove-a-wall-to-open-up-a-kitchen/` | AEO Q&A |

### Form notification wiring (live)

| Form | ID | Notification | Hook ID |
|---|---|---|---|
| `estimate` | `6a08924e0428cd0008f04abc` | email → `howerenovationsllc@gmail.com` on `submission_created` | `6a0892c972c0ceac9a8a45ac` |

Submissions hit Mike's Gmail and also stay in the Netlify Forms dashboard. To add a CC, POST another `email` hook to `/api/v1/hooks` with the same `form_id` + a different email. To pause notifications without deleting the hook, PATCH the hook with `{"disabled": true}`.

---

## Decisions made

- **Host: Netlify** (Free tier). Vercel killed, Cloudflare Pages ruled out (no built-in form handling).
- **Account model:** Devon builds under Streck Ventures team → Mike reviews → Mike creates own Netlify account → invite as Owner → transfer site → point `howerenovations.com` DNS at Netlify.
- **Logo:** real logo cropped from the live site's home page (screenshot via Devon, alpha-masked via PowerShell + System.Drawing). Source asset is only 156×127 — fine for header use at ~50px tall, will look soft if scaled larger. **Need a high-res source from Mike for production.**
- **Color palette pivot:** ember/amber accent replaced with `salmon` (300–700 scale) sampled from the logo's coral pixels (RGB ~249,199,135). The whole site now tonally matches the brand mark.
- **Phone:** 636-697-2408 (St. Louis / O'Fallon area code, from live site).
- **Service area:** O'Fallon, MO and surrounding St. Louis metro. The earlier "Central NH" location was wrong (Buzzfile data mismatch on a similarly-named LLC) — discarded everywhere.
- **Hero tagline:** "Make your house a home." (Mike's stated preference). Secondary "We build decks and other stuff!" used as a quote accent in About.
- **Service categories** rebuilt to match Mike's actual work: Decks & Outdoor / Kitchens / Bathrooms / Carpentry & Built-ins.
- **Testimonial section removed** entirely (no real testimonials available yet — section will return when Mike provides them).
- **AEO + SEO foundation shipped** (Tier 1 + Tier 2):
  - JSON-LD schema: `HomeAndConstructionBusiness` + `OfferCatalog`/`Service` on home, `FAQPage` (6 questions) on home, `BreadcrumbList` everywhere, `ItemList` of 6 projects on gallery, `FAQPage` on each Q&A page, `HomeAndConstructionBusiness` scoped to each city on area pages.
  - OG + Twitter card meta on both core pages and all 8 new pages.
  - `sitemap.xml` (10 URLs) and `robots.txt` at root.
  - 3 service-area pages (O'Fallon, St. Charles, St. Peters).
  - 5 answer-engine Q&A pages (composite vs wood, bathroom timeline, spotting rot, repair vs replace, kitchen wall removal). Each: direct answer up top, 600–900 words of body, related-question cross-links, CTA, FAQ schema.
  - Alt text audit on home — every photo has a descriptive alt (not "Composite deck" but "Second-story composite deck with aluminum rails and white lattice skirting").
  - All canonical URLs use the netlify preview domain for now — to update once `howerenovations.com` DNS points at Netlify (do a find/replace on `howe-renovations-preview.netlify.app` → `howerenovations.com` across the codebase).

---

## What exists

| File | Purpose |
|---|---|
| `index.html` | Hero (P5 deck bg, "Make your house a home"), Recent Transformations carousel (12 After photos cycling, 5s, pause-on-hover, prev/next + dot nav), Services (4 cards on Mike's real work), Featured Work (3 case-study teasers linking to gallery anchors), About ("We build decks and other stuff!" quote, 3 differentiators), Contact (Netlify Forms wired with honeypot — notification email NOT yet configured) |
| `gallery.html` | Six project case studies rendered from JS data: title + category badge + Mike's full Facebook writeup + Before/During/After photo grids, with lightbox + filter chips (All / Decks / Kitchens / Baths / Carpentry) |
| `brand/howe-logo.png` | Alpha-masked logo, 156×127, transparent bg. Used in header (h-12), mobile menu (h-10), footer (h-8), favicon |
| `brand/howe-logo-raw.png` | Source screenshot crop (dark bg intact) — keep as a backup |
| `README.md` | POC stack notes |
| `instructions-for-mike.txt` | Client-facing FB-export instructions + 6 business questions |
| `Descriptions/Project N/Project N Description.txt` | Mike's verbatim writeups for all 6 projects |
| `Images/Project N (Before\|build\|Build\|After)/` | Mike's real photos, all 6 projects. Note: P1-3 use lowercase `build`, P4-6 use capital `Build`. Both work on Netlify. |
| `areas/<city>/index.html` | 3 city landing pages (O'Fallon, St. Charles, St. Peters) — full Tailwind + schema |
| `answers/<slug>/index.html` | 5 AEO Q&A pages — direct answer + 600–900-word body + FAQ schema |
| `sitemap.xml` + `robots.txt` | At root. Sitemap lists all 10 discoverable URLs. Robots allows all + points at sitemap + disallows the raw screenshot logo. |
| `.gitignore` | Excludes `.vercel`, `.netlify` |

## Stack

- Static HTML + Tailwind via CDN (custom salmon palette in inline config)
- Vanilla JS for carousel (intersection-observer pause), gallery filter, lightbox, mobile menu — no libraries
- All photography is Mike's real work (no Unsplash placeholders remain on either page)
- Google Fonts (Inter + Fraunces)
- No build step

---

## Project map (gallery case studies)

| # | Title | Category | Before / Build / After |
|---|---|---|---|
| 1 | Rotted Deck + Subfloor Rescue | Decks | 6 / 5 / 5 |
| 2 | Custom Oak Staircase Rebuild | Carpentry | 2 / 14 / 4 |
| 3 | Stone Mantel + Hidden Wiring | Carpentry | 1 / 1 / 2 |
| 4 | Full Bathroom Gut + Re-Vent | Bathrooms | 3 / 7 / 1 |
| 5 | Composite Deck Replacement | Decks | 6 / 1 / 6 |
| 6 | Butcher Block + Open Layout | Kitchens | 2 / 2 / 2 |

---

## Next session

**Waiting on Mike's feedback from the review checklist (`mike-review-checklist.txt`).** When he responds, his answers go into one of three buckets:

### Bucket A — site-content edits driven by Mike's answers
Likely items he'll flag:
- License/insurance language correction (footer says "Licensed & insured" — soften or qualify if not literally true everywhere we claim service)
- Service-area list — add/remove cities he confirms/excludes (currently O'Fallon, St. Charles, St. Peters + St. Louis metro)
- Phone confirmation (currently 636-697-2408)
- Specific corrections to the 5 Q&A pages (the bathroom 3-week breakdown, the 5-point rot inspection, the 25%-rotted-or-replace rule, etc.)
- Specific corrections to the 6 homepage FAQ schema answers
- Voice/tone tweaks on the About section once he answers the 6 questions in `instructions-for-mike.txt`

### Bucket B — content assets to integrate
- **High-res logo** (current 156×127 crop is soft at hero size). Drop it in `brand/howe-logo.png`, redeploy.
- **Real testimonials** (1-3 short quotes). Add back the testimonial section that was removed earlier this session.
- **Phone-shot videos** of jobs in progress, if any. Add a video section or embed in the gallery.
- **Financing info** (GreenSky/Hearth/etc.) if Mike offers it. New section in services or About.

### Bucket C — ops/handoff (Devon-owned, not Mike)
- **Live walk-through of the Hydra widget with Mike.** Open the site, click the chat bubble, ask a few representative questions — "how long does a bathroom remodel take," "do you serve St. Charles," "what's the difference between composite and wood deck" — to verify the RAG path hits the AEO content. Show Mike his Hydra inbox so he can see conversations land there.
- **Rotate the leaked Netlify PAT** (`nfp_Gk7…3bz476c`, exposed in 2026-05-15 transcript). Now that Devon has run `netlify login` (OAuth, no PAT needed for CLI), the leaked PAT is safe to revoke. Netlify UI → User settings → Applications → Personal access tokens → revoke. If MCP still uses it, also `claude mcp remove netlify --scope user` + re-add via PowerShell with a fresh PAT.
- **Wire Netlify GitHub auto-deploy before transferring to Mike.** Right now the site is CLI-deployed only — `git push` does nothing, every deploy requires `netlify deploy --prod --site=3d292da9-… --dir=.`. Mike won't have a CLI workflow. Netlify dashboard → Site settings → Build & deploy → Continuous deployment → Link repository (`DarthDevon/home-improvement-poc`, default branch `main`, build command empty, publish dir `.`). After link, future GitHub pushes auto-deploy.
- **Domain transition** when Mike approves: he creates own Netlify account → invite as Owner → transfer site → point `howerenovations.com` DNS at Netlify. All canonical URLs / OG URLs / sitemap URLs / schema `@id` fields are currently using `howe-renovations-preview.netlify.app` — do a find/replace across the codebase to `howerenovations.com` after the DNS flip.
- **Image optimization** (deferred — only if speed is an actual complaint): the gallery loads ~60 full-res FB photos. Consider Netlify Image CDN (`/.netlify/images?url=...&w=900`) or a one-time compression pass.

### Resume command
- Say "let's continue on home-improvement-poc" — I'll do a Project State Read first.
- Or be specific: "Mike said X about Y, update it" — I'll find Y and apply the edit.

---

## Outstanding from Mike

- **High-res logo** (current crop is 156×127 from screenshot).
- **Real testimonials** (1–3 short quotes from past clients) — testimonial section is currently removed.
- Answers to the 6 questions in `instructions-for-mike.txt` (services list refinement, service area specifics, years in business, differentiation, contact preferences, testimonials/logo source).
- **Confirmation:** replace `howerenovations.com` with new site, or run parallel preview first?
