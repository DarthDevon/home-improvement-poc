---
Date: 2026-05-16
Note: **Hydra chat widget installed on all 10 pages.** Embed snippet `<script src="https://app.hydra-help.com/widget.js" data-tenant="howe-renovations-crw9" data-widget="howe-renovations-bd26c1"></script>` placed just before `</body>` in `index.html` + `gallery.html` + the 3 `areas/<city>/index.html` + the 5 `answers/<slug>/index.html`. Salmon `#F9C787` to match the logo. Attached to Mike's default Hydra Support Bot. Tracking + bot-visitor-context both enabled, so the bot sees what page each visitor is on. Knowledge source = the marketing site itself (`crawl_all=true` over the Netlify preview URL); 19 chunks indexed across home, gallery case-studies, the 3 service-area pages, and the 5 AEO Q&A pages. Mike's Hydra tenant slug is `howe-renovations-crw9` (id `706f5877-…`). Reference: deploy `6a08fb455d1014e174c6b9cc` 2026-05-16. To change the widget look or message, edit `widget_configs` row id `057b3975-11bd-4179-a79e-753bfce2ea7a` in Hydra (color, welcome_message, placeholder_text are all PATCH-able via `/api/widgets`).
---

---
Date: 2026-05-16
Note: **This Netlify site is CLI-deployed, NOT GitHub-auto-deployed.** Pushing to `DarthDevon/home-improvement-poc` `main` on GitHub does NOT trigger a Netlify build. Production deploys require `netlify deploy --prod --site=3d292da9-cbe4-4f18-bce5-0b83360a54b9 --dir=. --message="..."` from inside the project directory (or `netlify deploy --prod` once `netlify link` has linked the dir, which it already is). Symptom of the gap: pushed embed snippet to GitHub, curl against the production URL kept returning old HTML until manual `netlify deploy --prod` ran. Wire the GitHub connection in the Netlify dashboard (Site settings → Build & deploy → Continuous deployment → Link repository) before Mike takes ownership — he won't have a CLI workflow, so the site needs auto-deploy from his GitHub fork after transfer.
---

---
Date: 2026-05-16
Note: **Howe Renovations production identifiers (reference card).** Netlify site ID: `3d292da9-cbe4-4f18-bce5-0b83360a54b9`, name `howe-renovations-preview`, team `devonstreckfuss` (Streck Ventures, Free tier). Live URL: https://howe-renovations-preview.netlify.app. Estimate form ID: `6a08924e0428cd0008f04abc` (fields: name/phone/email/project_type/message + honeypot `bot-field`). Email notification hook ID: `6a0892c972c0ceac9a8a45ac` routes `submission_created` → `howerenovationsllc@gmail.com` (Mike's business inbox). GitHub: `DarthDevon/home-improvement-poc` (private). Custom domain to come: `howerenovations.com` (registered in Mike's name; DNS flip pending). Phone in use: 636-697-2408. Color palette: salmon (300=#FBD7B2 / 400=#F9C787 / 500=#EE9F5C / 600=#D67A3D / 700=#B85F2C) sampled from the logo coral pixels (RGB ~249,199,135).
---

---
Date: 2026-05-16
Note: **Photo folder case mismatch — Project 1-3 use lowercase `build`, Project 4-6 use capital `Build`.** Verified via `git ls-files | grep -oE "Project [0-9] \([A-Za-z]+\)" | sort -u`. On Windows it's a no-op (case-insensitive FS), but Netlify CDN is case-sensitive on Linux. Both case variants happen to resolve 200 on the live CDN (likely because the Windows FS exported both names during the API upload). The gallery `renderProject` function carries a `buildCase` field per project (`build` for P1-3, `Build` for P4-6) to construct URLs correctly. If renaming for consistency, use `git mv -f <old> <new>` to make Git on Windows actually track the case change.
---

---
Date: 2026-05-16
Note: **Logo source: cropped from a 156×127 screenshot of `howerenovations.com/home`.** No higher-res source exists in the project. Mike's live site is a Bookmark Connect builder template where the logo is assembled from individual SVG shape primitives on bcassetcdn.com — not downloadable as a unified mark. The PNG at `brand/howe-logo.png` is alpha-masked via PowerShell + System.Drawing (luminance threshold 20-80) so the dark builder background drops to transparent. Fine for header (h-12 = 48px tall, well within source resolution), gets soft at hero/print sizes. `brand/howe-logo-raw.png` is the original dark-bg screenshot kept as backup. Open ask in `mike-review-checklist.txt`: get a higher-res logo from Mike for larger surface use.
---

---
Date: 2026-05-16
Note: **POC repo already linked to Vercel from yesterday's deploy.** `.vercel/project.json` carries `projectId: prj_UOIzCYGkROZALm6RG77MgDEJeNwd`, `orgId: team_sXYqyL0jetkbAnEfRfhCbx7z`, `projectName: home-improvement-poc`. Decision in 2026-05-16 session: pivot to Netlify (commercial-use TOS + Netlify Forms for the demo-signup form). Kill the Vercel project before/during Netlify deploy so the site doesn't live in two places and the `home-improvement-poc.vercel.app` URL doesn't linger. Either `vercel remove home-improvement-poc --yes` from this folder or via Vercel dashboard. Don't just abandon — orphan projects clutter the team list.
---

---
Date: 2026-05-16
Note: **Mike's existing site `howerenovations.com` is a stock template — "WELCOME" + "GET IN TOUCH" only, no real content.** Verified via WebFetch 2026-05-16. The current POC (`index.html` + `gallery.html`) with Unsplash placeholders is already a massive visual upgrade. Implication: we can deploy the POC essentially unchanged for first review and Mike will see clear improvement BEFORE he sends his Facebook content. Don't gate first preview on Mike's content; gate the final content swap on it.
---

---
Date: 2026-05-16
Note: **Client identity confirmed via web search.** Business: Howe Renovations (also appears as "Howe Home Improvement" in some directories). Owner: Mike. Location: 40 Winchester Dr, Center Barnstead, NH 03225. Phone: (603) 776-0611. FB Page: `facebook.com/pages/category/Contractor/Howe-Home-Improvement-134086539948962/`. Existing site: `howerenovations.com`. Same phone (603) 776-0611 also listed under "603 Coatings LLC" on Buzzfile — likely his registered LLC name. Tagline he mentioned to Devon: "Make your house a home" (not yet on the live site).
---
