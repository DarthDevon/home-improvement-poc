# Howe Renovations POC — Project State

**Status:** 🟢 **LIVE at `https://howerenovations.com`** (2026-05-28). Domain cutover complete, SSL provisioned, CD pipeline wired end-to-end, Hydra knowledge source re-crawled on the new domain. Awaiting Mike's content feedback from the review checklist (`mike-review-checklist.txt`).
**Last updated:** 2026-05-28
**Last deploy:** `6a190e87545cc7a3c36b7eef` (2026-05-29 03:57 UTC) — commit `884458b` (canonical URL sweep preview→live), built via webhook CD in 5s.
**Site ID:** `3d292da9-cbe4-4f18-bce5-0b83360a54b9` (Netlify team `devonstreckfuss` / "Streck Ventures", Free tier — 300 credits/mo budget; this site projects ~30 credits/mo steady-state).
**Repo:** `DarthDevon/home-improvement-poc` — **public** (flipped from private 2026-05-28 to sidestep Netlify Free-plan webhook-deploy contributor block).
**Hydra integration (tenant `howe-renovations-crw9`):** widget slug `howe-renovations-bd26c1` · color `#F9C787` salmon · bot "Support Bot" (`db5eb841-…`) · tracking + bot-visitor-context enabled · knowledge source `38f39669-5ebd-40cb-a4fa-3e74444dfad4` crawls `https://howerenovations.com` with `crawl_all=true` (19 chunks, re-crawled 2026-05-28).

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
| **Live site** | **https://howerenovations.com** ✅ (also `www.` → 301 → apex) |
| Netlify-fallback URL | https://howe-renovations-preview.netlify.app (still works) |
| Netlify admin | https://app.netlify.com/projects/howe-renovations-preview |
| Netlify Forms admin | https://app.netlify.com/projects/howe-renovations-preview/forms |
| GitHub repo | https://github.com/DarthDevon/home-improvement-poc (**public** as of 2026-05-28) |
| Sitemap | https://howerenovations.com/sitemap.xml |
| robots.txt | https://howerenovations.com/robots.txt |

## DNS / SSL

- **Registrar:** BrandCrowd (Design.com reseller, ultimately on GoDaddy domaincontrol.com infrastructure). Renewal: 2026-08-17.
- **Nameservers:** Netlify DNS (`dns1-4.p08.nsone.net`) — swapped at BrandCrowd Portfolio → howerenovations.com → Nameservers tab.
- **DNS zone (Netlify):** `6a17cef390c2d217f6d89400` — apex + www auto-provisioned as NETLIFY-type records.
- **SSL:** Let's Encrypt, CN=howerenovations.com. Auto-renewed by Netlify.
- **Email:** NO MX records — Howe doesn't receive mail at `@howerenovations.com`. Defensive DMARC TXT exists at BrandCrowd's nameservers but is no-op without MX. Form submissions still route to `howerenovationsllc@gmail.com` via Netlify Forms.

## Deploy pipeline

- **CD wired:** `git push origin main` → Netlify webhook → build in ~5s (no build command, publish from repo root).
- **Build config** lives in `netlify.toml`: `publish='.'`, `command=''`, plus `[[redirects]]` returning 404 for internal docs (`project.md`, `LESSONS*.md`, `README.md`, `CLAUDE.md`, `mike-review-checklist.txt`, `instructions-for-mike.txt`, `Descriptions/*`).
- **Production branch:** `main`. Branch deploys for any other branch get free preview URLs (`https://<branch>--howe-renovations-preview.netlify.app`).
- **STOP using `netlify deploy --prod`** — CLI deploys bypass the netlify.toml redirects (raw upload of `--dir=.`) AND each one costs 15 credits unnecessarily.
- **Credit budget:** Netlify Free (300 credits/mo, $0). Steady-state usage on this site: ~30 credits/mo (1-2 prod deploys × 15 + negligible bandwidth/requests). Plenty of headroom for the team's other site (2ladypainters) on the same budget.

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
- **Live walk-through of the Hydra widget with Mike.** Open the site at the LIVE `howerenovations.com` URL, click the chat bubble, ask a few representative questions — "how long does a bathroom remodel take," "do you serve St. Charles," "what's the difference between composite and wood deck" — to verify the RAG path hits the AEO content. Show Mike his Hydra inbox so he can see conversations land there. (Re-crawled 2026-05-28 on the new domain — 19 chunks, 16 reference the live URL.)
- **Rotate the leaked Netlify PAT** (`nfp_Gk7…3bz476c`, exposed in 2026-05-15 transcript). Now that Devon has run `netlify login` (OAuth, no PAT needed for CLI), the leaked PAT is safe to revoke. Netlify UI → User settings → Applications → Personal access tokens → revoke. If MCP still uses it, also `claude mcp remove netlify --scope user` + re-add via PowerShell with a fresh PAT.
- ✅ ~~Wire Netlify GitHub auto-deploy~~ — DONE 2026-05-28. CD pipeline live; details in "Deploy pipeline" section above.
- ✅ ~~Domain transition~~ — DONE 2026-05-28. Live at `howerenovations.com`. Canonical URL sweep complete (commit `884458b`).
- **Eventual transfer to Mike** (no rush — keep on Devon's account until Mike asks). When Mike wants ownership: he creates his own Netlify account → invite as Owner on Streck Ventures → transfer site → his free 300-credit budget covers his own deploys → can remove from Streck Ventures team afterward. NOTE the repo is now public on GitHub — Mike can fork it before transfer if he wants his own GitHub copy too.
- **Image optimization** (deferred — only if speed is an actual complaint): the gallery loads ~60 full-res FB photos. Consider Netlify Image CDN (`/.netlify/images?url=...&w=900`) or a one-time compression pass.

### Resume command
- Say "let's continue on home-improvement-poc" — I'll do a Project State Read first.
- Or be specific: "Mike said X about Y, update it" — I'll find Y and apply the edit, push to main, CD auto-deploys in ~5s.

### How to make site edits going forward

1. Make changes locally in `C:/Users/eliza/Claudes/architect/projects/home-improvement-poc/`.
2. For iteration: create a branch (`git checkout -b mike-edits-YYYY-MM-DD`), push, Netlify auto-generates a free branch-preview URL at `https://<branch>--howe-renovations-preview.netlify.app`. Iterate freely — 0 credits per branch deploy.
3. When ready to ship: `git checkout main && git merge <branch> && git push origin main` → CD fires, live in ~5s. **15 credits per merge to main**.
4. NEVER `netlify deploy --prod` — bypasses netlify.toml, costs credits, and we're moving off it permanently.

### After significant content changes, re-crawl Hydra knowledge

If you edit substantial body text on the site (not just typos), trigger a Hydra re-crawl so the widget cites fresh content. Two paths:
- From Hydra app UI (cleanest if you have admin access to Mike's tenant): Knowledge Sources → "Howe Renovations marketing site" → Re-crawl.
- One-shot tsx script in `hydra/scripts/` that imports `ingestSource` directly — pattern documented in Hydra LESSONS (grep: `re-crawl URL knowledge source via tsx-import ingestSource`).

---

## Outstanding from Mike

- **High-res logo** (current crop is 156×127 from screenshot).
- **Real testimonials** (1–3 short quotes from past clients) — testimonial section is currently removed.
- Answers to the 6 questions in `instructions-for-mike.txt` (services list refinement, service area specifics, years in business, differentiation, contact preferences, testimonials/logo source).
- **Confirmation:** replace `howerenovations.com` with new site, or run parallel preview first?
