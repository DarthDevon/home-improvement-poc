# Howe Renovations POC — Project State

**Status:** POC built, hosting decision made (Netlify), Netlify MCP installed, ready for first deploy.
**Last updated:** 2026-05-16
**Last deploy:** Vercel `home-improvement-poc.vercel.app` (2026-05-15) — to be killed, replaced by Netlify.

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

## Decisions made this session

- **Host: Netlify** (free Starter tier).
  - Rejected Vercel — Hobby tier is non-commercial; Pro is $20/mo.
  - Rejected Cloudflare Pages — no built-in form handling; would need a Worker for the demo-signup form.
  - Netlify Forms ships free (100 submissions/mo) and handles the demo-signup form with zero backend.
- **Account model:** Devon builds under his own Netlify account → deploys to free preview URL → Mike reviews → Mike creates own account → invite as Owner → transfer site. Domain (`howerenovations.com`) stays in Mike's name throughout.
- **Content acquisition:** Mike will export FB content via FB's "Download Your Information" tool. Instructions saved at `instructions-for-mike.txt` for Devon to forward.
- **Netlify MCP:** installed at user scope in Claude Code (`@netlify/mcp` via npx, Devon's PAT). Requires Claude Code restart for `netlify_*` tools to appear.

---

## What exists

| File | Purpose |
|---|---|
| `index.html` | Hero, services, featured work, about, testimonial, contact (placeholder copy + Unsplash photos) |
| `gallery.html` | Full gallery with category filter + lightbox |
| `README.md` | POC stack notes + swap-for-real-site checklist |
| `instructions-for-mike.txt` | Client-facing instructions for FB content export + 6 business questions |
| `.gitignore` | Excludes `.vercel` |
| `.vercel/project.json` | Leftover Vercel link (to be removed when project is killed) |
| `Images/Project 1 (Before)/` | 6 photos from Mike — Project 1 pre-renovation (FB-source filenames preserved) |
| `Images/Project 1 (build)/` | 5 photos from Mike — Project 1 during construction |
| `Images/Project 1 (After)/` | 5 photos from Mike — Project 1 finished |
| `Descriptions/` | Empty — Mike still owes written descriptions |

## Stack

- Static HTML + Tailwind via CDN
- Vanilla JS for gallery filter + lightbox
- Unsplash placeholder photography
- Google Fonts (Inter + Fraunces)
- No build step

---

## Next session

1. **Restart Claude Code** so the Netlify MCP loads its tools (`netlify_create_site`, `netlify_deploy`, etc.).
2. **Rotate the leaked PAT** (token `nfp_Gk7XDTYcz1LJ62JQmvKFCCmhUcCU43bz476c` is in this session's transcript). In Netlify: User settings → Applications → Personal access tokens → revoke `Claude Code MCP` → generate new → `claude mcp remove netlify --scope user` + re-add via PowerShell (token never enters chat).
3. **Init git + push to GitHub** at `DarthDevon/home-improvement-poc` (private) — done as part of this `/learn`.
4. **Kill the Vercel project**: `vercel remove home-improvement-poc --yes` from this folder (to free the name + avoid two-host drift).
5. **Deploy POC to Netlify via MCP**: create site `howe-renovations-preview` (or similar), deploy from this folder, confirm live at `<name>.netlify.app`.
6. **Send Mike** the preview URL + `instructions-for-mike.txt`.

After Mike returns content:
- Swap Unsplash images for his real photos in `gallery.html` + `index.html`.
- Rewrite copy in his voice; add "Make your house a home" tagline.
- Wire demo-signup form to Netlify Forms (`<form data-netlify="true">`), set notification email to Mike + Devon.
- Mike creates Netlify account → invite as Owner → transfer site → point `howerenovations.com` DNS at Netlify.

---

## Outstanding from Mike

- **Partially delivered:** 16 Project 1 photos (Before/build/After) are in `Images/Project 1 *`. Additional projects + the rest of his FB photo library still pending.
- Written descriptions for each project (folder `Descriptions/` is currently empty)
- Answers to the 6 questions in `instructions-for-mike.txt` (services list, service area, years in business, differentiation, contact preferences, testimonials/logo)
- Confirmation: replace `howerenovations.com` with new site, or run parallel preview first?
