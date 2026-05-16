# Howe Renovations POC — Project State

**Status:** v2 deployed — real logo, all 6 projects wired in as case studies, hero carousel of best After photos cycling, salmon palette pulled from Mike's logo. Ready to send to Mike for design review.
**Last updated:** 2026-05-16
**Last deploy:** Netlify `howe-renovations-preview.netlify.app` — deploy `6a088f0a228bf9d50fd98f5e` (2026-05-16, state: ready, 62 files, 5s).
**Site ID:** `3d292da9-cbe4-4f18-bce5-0b83360a54b9` (Netlify team `devonstreckfuss` / "Streck Ventures", Free tier).

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

1. **Send Mike the preview URL** (`https://howe-renovations-preview.netlify.app`). It's lived-in — real photos, real logo, real project writeups, correct location (O'Fallon, MO).
2. **Rotate the leaked Netlify PAT** (`nfp_Gk7…3bz476c`, exposed in 2026-05-15 transcript). Netlify UI → User settings → Applications → Personal access tokens → revoke `Claude Code MCP` → generate new → `claude mcp remove netlify --scope user` + re-add via PowerShell.
4. **Get a high-res logo from Mike** — the 156×127 crop works for header use but won't hold up at large sizes (hero brand, business cards, etc.). Ask for the original Facebook/builder source if he has it.
5. **Get real testimonials** (1–3 short quotes from past clients). The testimonial section was removed entirely — add it back when content is available.
6. **Image optimization** (deferred — only if performance matters): the gallery loads ~60 full-res FB photos. Total page weight is significant. If Mike complains about loading speed, consider Netlify Image CDN (`/.netlify/images?url=...&w=900`) or a build-step compression pass.
7. **Domain transition:** Mike creates Netlify account → invite as Owner → transfer site → point `howerenovations.com` DNS at Netlify.

---

## Outstanding from Mike

- **High-res logo** (current crop is 156×127 from screenshot).
- **Real testimonials** (1–3 short quotes from past clients) — testimonial section is currently removed.
- Answers to the 6 questions in `instructions-for-mike.txt` (services list refinement, service area specifics, years in business, differentiation, contact preferences, testimonials/logo source).
- **Confirmation:** replace `howerenovations.com` with new site, or run parallel preview first?
