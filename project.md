# Howe Renovations POC — Project State

**Status:** POC deployed to Netlify; preview URL ready to send to Mike. Vercel project killed. First batch of Mike's real content (Project 1 description + Project 2 photos) in repo.
**Last updated:** 2026-05-16
**Last deploy:** Netlify `howe-renovations-preview.netlify.app` — deploy `6a0884d8143b7609c71e30d6` (2026-05-16, state: ready, 26 files, 7s).
**Site ID:** `3d292da9-cbe4-4f18-bce5-0b83360a54b9` (Netlify team `devonstreckfuss` / "Streck Ventures", Free tier).

---

## Client

| Field | Value |
|---|---|
| Business | Howe Renovations (aka Howe Home Improvement) |
| Owner | Mike |
| Location | 40 Winchester Dr, Center Barnstead, NH 03225 |
| Phone | (603) 776-0611 |
| FB Page | `facebook.com/pages/category/Contractor/Howe-Home-Improvement-134086539948962/` |
| Existing site | `howerenovations.com` — stock template, "WELCOME" + contact button only |
| Tagline (per Mike) | "Make your house a home" — not yet on live site |
| Likely registered LLC | `603 Coatings LLC` (same phone, per Buzzfile) |

---

## Live URLs

| Surface | URL |
|---|---|
| Preview (share with Mike) | https://howe-renovations-preview.netlify.app |
| Netlify admin | https://app.netlify.com/projects/howe-renovations-preview |
| GitHub repo | https://github.com/DarthDevon/home-improvement-poc (private) |
| Future custom domain | howerenovations.com (Mike's; point DNS at Netlify when ready) |

---

## Decisions made

- **Host: Netlify** (Free tier).
  - Rejected Vercel — Hobby tier is non-commercial; Pro is $20/mo.
  - Rejected Cloudflare Pages — no built-in form handling.
  - Netlify Forms ships free (100 submissions/mo) and handles the demo-signup form with zero backend.
- **Account model:** Devon builds under his Streck Ventures Netlify team → deploys to free preview URL → Mike reviews → Mike creates own account → invite as Owner → transfer site. Domain (`howerenovations.com`) stays in Mike's name throughout.
- **Content acquisition:** Mike will export FB content via FB's "Download Your Information" tool. Instructions at `instructions-for-mike.txt`. First batch already in (Project 1 description text, Project 2 Before + build photos).
- **Netlify MCP:** installed at user scope; `create-new-project` and `deploy-site` operations confirmed working in this session via the `@netlify/mcp` server.

---

## What exists

| File | Purpose |
|---|---|
| `index.html` | Hero, services, featured work, about, testimonial, contact (placeholder copy + Unsplash photos) |
| `gallery.html` | Full gallery with category filter + lightbox |
| `README.md` | POC stack notes + swap-for-real-site checklist |
| `instructions-for-mike.txt` | Client-facing instructions for FB content export + 6 business questions |
| `Descriptions/Project 1/Project 1 Description.txt` | Mike's write-up of a rotted-deck-and-subfloor rebuild — usable as Project 1 case study copy |
| `Images/Project 1 (Before\|build\|After)/` | Mike's real photos for Project 1 (16 photos total) |
| `Images/Project 2 (Before\|build)/` | Mike's real photos for Project 2 (After folder + description still pending) |
| `.gitignore` | Excludes `.vercel`, `.netlify` |

## Stack

- Static HTML + Tailwind via CDN
- Vanilla JS for gallery filter + lightbox
- Unsplash placeholder photography (to be swapped for Mike's real photos)
- Google Fonts (Inter + Fraunces)
- No build step

---

## Next session

1. **Send Mike the preview URL** (`https://howe-renovations-preview.netlify.app`) + `instructions-for-mike.txt`. Note: site still has placeholder copy + Unsplash photos — make that explicit so he knows what to react to.
2. **Rotate the leaked PAT** (token `nfp_Gk7XDTYcz1LJ62JQmvKFCCmhUcCU43bz476c` is in 2026-05-15 transcript). In Netlify: User settings → Applications → Personal access tokens → revoke `Claude Code MCP` → generate new → `claude mcp remove netlify --scope user` + re-add via PowerShell (token never enters chat).
3. **Wire up real Project 1 + Project 2 content** in `gallery.html` + `index.html`:
   - Project 1: subtitle "Rotted deck + spongy subfloor rebuild" (per Mike's description). Use Before/build/After folders.
   - Project 2: ask Mike for After photos + a written description in the same format.
   - Replace at least 2 Unsplash placeholders on the home page with Project 1 hero shots so the preview looks lived-in.
4. **Once Mike answers the 6 questions** in `instructions-for-mike.txt`:
   - Rewrite copy in his voice; add "Make your house a home" tagline.
   - Wire demo-signup form to Netlify Forms (`<form data-netlify="true">`), set notification email to Mike + Devon.
5. **When Mike approves the design:** Mike creates Netlify account → invite as Owner → transfer site → point `howerenovations.com` DNS at Netlify (custom domain config in Netlify admin).

---

## Outstanding from Mike

- **Partially delivered:** 16 Project 1 photos (Before/build/After) + Project 1 written description + Project 2 Before/build photos.
- **Still pending for Project 2:** After photos + written description in the same format as Project 1's.
- Additional projects + the rest of his FB photo library still pending.
- Answers to the 6 questions in `instructions-for-mike.txt` (services list, service area, years in business, differentiation, contact preferences, testimonials/logo).
- Confirmation: replace `howerenovations.com` with new site, or run parallel preview first?
