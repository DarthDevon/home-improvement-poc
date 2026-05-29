# Howe Renovations POC — LESSONS Index

**Read this at session start instead of `LESSONS.md`.** Full lesson bodies live in `LESSONS.md`. When a topic below matches the current task, `Grep LESSONS.md` for the keyword in parentheses.

**Maintenance:** the `/learn` skill appends a one-liner here whenever it appends to `LESSONS.md`.

---

## Recent entries

- 2026-05-28 — **Howe knowledge source re-crawled on new domain (19 chunks, 16 referencing howerenovations.com).** Update `knowledge_sources.url` via Mgmt API, then tsx-import `ingestSource` (proxy.ts blocks curl+cron-secret on /api/knowledge/ingest) (grep: "Howe knowledge source re-crawl via tsx script")
- 2026-05-28 — **Canonical URLs swept preview→live across 12 files via `sed -i`.** 85 occurrences. Internal docs (project.md, LESSONS.md, etc.) intentionally untouched as historical record (grep: "Howe canonical URL find/replace from preview to live")
- 2026-05-28 — **Repo flipped public to sidestep Netlify Free private-repo contributor block.** No secrets in repo; netlify.toml redirects still 404 internal docs at the public site URL (grep: "home-improvement-poc repo flipped public")
- 2026-05-28 — **netlify.toml `[[redirects]] status=404 force=true` per internal doc.** Required because publish='.' deploys whole repo. CLI `netlify deploy --dir=.` BYPASSES these redirects — only CD-triggered builds get the protection (grep: "netlify.toml redirects 404 internal docs publish='.'")
- 2026-05-28 — **CD wired end-to-end. Setup sequence + "unrecognized Git contributor" fix.** updateSite repo block → install Netlify GitHub App on the specific repo → Members → Git Contributors → Connect GitHub (free path; auto-approve toggle is paid) (grep: "Howe CD wiring + Git Contributors fix")
- 2026-05-28 — **howerenovations.com live via Netlify DNS using NS1 nameservers `dns1-4.p08.nsone.net` (p08 shard zone-specific).** Nameserver delegation lives at BrandCrowd Portfolio → domain → Nameservers tab, NOT in DNS Records table. No MX = email-safe (grep: "howerenovations.com nameserver swap via BrandCrowd")
- 2026-05-16 — **Hydra chat widget installed on all 10 pages (slug `howe-renovations-bd26c1`).** Salmon `#F9C787`, attached to Mike's default Support Bot, tracking + visitor-context on. Knowledge source = the site itself (19 chunks). Edit widget via `widget_configs` id `057b3975-…` (grep: "Hydra chat widget installed on all 10 pages")
- 2026-05-16 — **Netlify site is CLI-deployed, NOT GitHub-auto-deployed.** `git push` doesn't trigger Netlify. Production deploys need manual `netlify deploy --prod --site=3d292da9-… --dir=.`. Wire the GitHub connection in Netlify dashboard before transfer to Mike (grep: "This Netlify site is CLI-deployed, NOT GitHub-auto-deployed")
- 2026-05-16 — **Production identifiers (reference card).** Site ID `3d292da9-…`, form ID `6a08924e-…`, hook ID `6a0892c9-…` → `howerenovationsllc@gmail.com`. Phone 636-697-2408. Salmon palette 300-700. (grep: "Howe Renovations production identifiers")
- 2026-05-16 — **Photo folder case mismatch.** P1-3 lowercase `build`, P4-6 capital `Build`. Gallery's `buildCase` field handles it; both cases resolve 200 on Netlify CDN. (grep: "Photo folder case mismatch")
- 2026-05-16 — **Logo is a 156×127 screenshot crop.** No higher-res source available — Mike's site is a builder template assembling the mark from CDN SVG primitives. Alpha-masked via PowerShell + System.Drawing. Fine for header, soft at hero size. (grep: "Logo source: cropped from a 156×127 screenshot")
- 2026-05-16 — **POC repo already linked to Vercel from yesterday's deploy.** `.vercel/project.json` carries `prj_UOIzCYGkROZALm6RG77MgDEJeNwd` under team_sXYqyL0jetkbAnEfRfhCbx7z. Pivot to Netlify in this session — kill the Vercel project (`vercel remove home-improvement-poc --yes`) before/during Netlify deploy so the site doesn't live in two places (grep: "POC repo already linked to Vercel")
- 2026-05-16 — **Mike's existing site `howerenovations.com` is a stock template ("WELCOME" + contact button only).** Current POC is already a massive upgrade with placeholders — first preview doesn't need to wait on Mike's FB content (grep: "Mike's existing site `howerenovations.com` is a stock template")
- 2026-05-16 — **Client identity CORRECTED.** Mike, Howe Renovations, **O'Fallon, MO** (St. Louis metro), **636-697-2408**. Earlier "Center Barnstead NH / 603-776-0611 / 603 Coatings LLC" was wrong — Buzzfile mismatch on a similarly-named LLC; Devon flagged. Tagline "Make your house a home" stands. FB page id 134086539948962 stands. (grep: "Client identity CORRECTED")
- 2026-05-16 — **Buzzfile is not a verification source.** A Buzzfile result that matched a similar business name + phone area code to "603 Coatings LLC" in NH was incorporated as ground truth and propagated through `project.md`, both HTML pages, and LESSONS for a full session before Devon caught it. Lesson: when the client's own live site (or a screenshot from Devon) shows a different city/area code, the live site wins. Buzzfile / OpenCorporates / similar aggregators are LEADS, not facts. (grep: "Buzzfile is not a verification source")

## Topic clusters

### Hydra integration
- **Chat widget on all 10 pages** — tenant slug `howe-renovations-crw9`, widget slug `howe-renovations-bd26c1`, knowledge source crawls the site itself (grep: "Hydra chat widget installed on all 10 pages")

### Deploy workflow
- **Netlify is CLI-deploy, not GitHub-auto** — wire GitHub connection before Mike takes ownership (grep: "This Netlify site is CLI-deployed") *(historical — superseded 2026-05-28 by full CD wiring below)*
- **CD wired 2026-05-28** — full setup sequence + the "unrecognized Git contributor" fix path (grep: "Howe CD wiring + Git Contributors fix")
- **netlify.toml redirects pattern** — 404 internal docs when publish='.', CLI deploys bypass (grep: "netlify.toml redirects 404 internal docs publish='.'")
- **Repo flipped public** — backstop for Netlify Free contributor check (grep: "home-improvement-poc repo flipped public")

### Domain / DNS
- **howerenovations.com cutover 2026-05-28** — NS1 nameservers `dns1-4.p08.nsone.net`, BrandCrowd Portfolio→domain→Nameservers tab, no MX to break (grep: "howerenovations.com nameserver swap via BrandCrowd")
- **Canonical URL sweep** — sed -i across 12 files, internal docs intentionally untouched (grep: "Howe canonical URL find/replace from preview to live")

### Hydra integration (Howe tenant)
- **Knowledge re-crawl after domain change** — Mgmt API UPDATE then tsx-import ingestSource (proxy blocks /api/knowledge/* cron-secret) (grep: "Howe knowledge source re-crawl via tsx script")

### Hosting decision
- **Pivoted from Vercel → Netlify** for commercial-use TOS + free built-in form handling (grep: "POC repo already linked to Vercel")

### Client / business identity
- **Mike, Howe Renovations, O'Fallon MO** (St. Louis metro), 636-697-2408 — full contact info CORRECTED 2026-05-16 (grep: "Client identity CORRECTED")
- **Existing site baseline** — `howerenovations.com` is a stock "WELCOME" template at the root URL, but `/home` has the real logo + tagline + phone. POC is an upgrade. (grep: "Mike's existing site `howerenovations.com` is a stock template")

### Research / verification hygiene
- **Buzzfile / OpenCorporates are leads, not facts** — propagating a Buzzfile name+phone match without client-side verification took a full session to unwind (grep: "Buzzfile is not a verification source")

### Production identifiers
- **All IDs in one place** (site / form / notification hook / phone / palette) (grep: "Howe Renovations production identifiers")

### Asset / file management
- **Photo folder case mismatch** — `build` vs `Build` per project (grep: "Photo folder case mismatch")
- **Logo provenance + resolution limit** (grep: "Logo source: cropped from a 156×127 screenshot")
