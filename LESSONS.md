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

---
Date: 2026-05-28
Note: **Domain `howerenovations.com` is LIVE on Netlify via Netlify DNS.** BrandCrowd (Design.com reseller of GoDaddy domaincontrol.com nameservers) → Portfolio → click domain → **Nameservers** tab (separate from DNS Records tab) → Change Nameservers → Custom → paste 4 NS1 nameservers Netlify gave us at zone creation: `dns1-4.p08.nsone.net` (p08 shard is zone-specific, don't guess). Propagation was essentially instant via Google/Cloudflare resolvers. Netlify auto-created apex `@` + `www` NETLIFY-type records pointing at the load balancer (no manual A/CNAME). Let's Encrypt SSL provisioned within ~5 min (initially served fallback `*.netlify.app` cert — `openssl s_client | x509 -subject` confirms when real cert takes over). Howe has NO MX records — verified before nameserver swap so the cutover didn't break Mike's email. DMARC TXT existed defensively but no mail routing. (grep: "howerenovations.com nameserver swap via BrandCrowd")
---

---
Date: 2026-05-28
Note: **CD wired — git push origin main now auto-deploys in ~5s.** Full setup sequence: (1) `netlify api updateSite` with `repo` block sets repo_url/branch/cmd/dir. (2) Devon installs Netlify GitHub App via https://github.com/apps/netlify → "Only select repositories" → home-improvement-poc → Install. This populates `build_settings.installation_id`. (3) First auto-build error: "Build blocked: unrecognized Git contributor" because repo is private + commit author not a verified contributor. (4) Devon clicks **Link Git account** button on the failed deploy page (or Team Settings → Members → Git Contributors → GitHub Connect). Once linked, future webhook deploys auto-approve. We ALSO flipped the repo to public (`gh repo edit DarthDevon/home-improvement-poc --visibility public --accept-visibility-change-consequences`) as a backstop, but the Git Contributors link was the actual fix. (grep: "Howe CD wiring + Git Contributors fix")
---

---
Date: 2026-05-28
Note: **`netlify.toml` ships with `[build] publish = "."` + `[[redirects]]` returning 404 for internal docs.** Pattern needed because publish='.' deploys the whole repo, including `project.md` / `LESSONS*.md` / `README.md` / `CLAUDE.md` / `mike-review-checklist.txt` / `instructions-for-mike.txt` / `Descriptions/*`. Each gets a `[[redirects]] from="/path" to="/" status=404 force=true` block. robots.txt mirrors the Disallow list. Verified post-deploy: `curl -o /dev/null -w "%{http_code}" https://howerenovations.com/project.md` returns 404 while `/` returns 200. **WARNING**: CLI `netlify deploy --dir=.` BYPASSES the netlify.toml redirects (raw file upload), so this protection only applies to CD-triggered builds. Don't use `--prod` deploys anymore. (grep: "netlify.toml redirects 404 internal docs publish='.'")
---

---
Date: 2026-05-28
Note: **Repo flipped to public (`DarthDevon/home-improvement-poc`).** Trade-off accepted: (a) sidesteps Netlify Free-plan "unrecognized Git contributor" check on private-repo CD; (b) site is genuinely public marketing content with no secrets in the repo (.gitignore excludes .vercel/.netlify; .env not in repo). project.md / LESSONS / mike-review-checklist.txt are GitHub-visible but contain no credentials — Mike's email + phone are already on the live site. The `netlify.toml` redirects above still hide those files at the public Netlify URL even though they're visible on GitHub. (grep: "home-improvement-poc repo flipped public")
---

---
Date: 2026-05-28
Note: **Canonical URLs swept from preview to live domain via `sed -i`.** 85 occurrences across 12 deploy-relevant files updated `howe-renovations-preview.netlify.app` → `howerenovations.com`. Bash one-liner: `find . -type f \( -name "*.html" -o -name "sitemap.xml" -o -name "robots.txt" \) -not -path "./.git/*" | while read f; do grep -q "OLD" "$f" && sed -i 's|OLD\.netlify\.app|NEW.com|g' "$f"; done`. Intentionally left untouched: project.md, LESSONS.md, mike-review-checklist.txt (historical record, 404'd at the public URL anyway). After push, Hydra knowledge source re-crawled to update the 19 chunks in its RAG index. (grep: "Howe canonical URL find/replace from preview to live")
---

---
Date: 2026-05-28
Note: **Hydra knowledge source for Howe (id `38f39669-5ebd-40cb-a4fa-3e74444dfad4`, tenant `706f5877-…`) re-crawled on new domain — 19 chunks indexed, 16 reference the new URL.** Step 1: `UPDATE knowledge_sources SET url = 'https://howerenovations.com' WHERE id = '...'` via Supabase Mgmt API. Step 2: trigger ingest. Cannot use curl + x-cron-secret on `/api/knowledge/ingest` — Hydra's proxy.ts redirects unauth requests to /auth/login BEFORE the route's cron-secret bypass runs. Working path: one-shot tsx script in `hydra/scripts/` that imports `ingestSource` directly and runs `npx tsx --env-file=.env.local scripts/...ts`. Same code the admin UI button calls. (grep: "Howe knowledge source re-crawl via tsx script")
---
