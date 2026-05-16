# Howe Renovations POC — LESSONS Index

**Read this at session start instead of `LESSONS.md`.** Full lesson bodies live in `LESSONS.md`. When a topic below matches the current task, `Grep LESSONS.md` for the keyword in parentheses.

**Maintenance:** the `/learn` skill appends a one-liner here whenever it appends to `LESSONS.md`.

---

## Recent entries

- 2026-05-16 — **POC repo already linked to Vercel from yesterday's deploy.** `.vercel/project.json` carries `prj_UOIzCYGkROZALm6RG77MgDEJeNwd` under team_sXYqyL0jetkbAnEfRfhCbx7z. Pivot to Netlify in this session — kill the Vercel project (`vercel remove home-improvement-poc --yes`) before/during Netlify deploy so the site doesn't live in two places (grep: "POC repo already linked to Vercel")
- 2026-05-16 — **Mike's existing site `howerenovations.com` is a stock template ("WELCOME" + contact button only).** Current POC is already a massive upgrade with placeholders — first preview doesn't need to wait on Mike's FB content (grep: "Mike's existing site `howerenovations.com` is a stock template")
- 2026-05-16 — **Client identity CORRECTED.** Mike, Howe Renovations, **O'Fallon, MO** (St. Louis metro), **636-697-2408**. Earlier "Center Barnstead NH / 603-776-0611 / 603 Coatings LLC" was wrong — Buzzfile mismatch on a similarly-named LLC; Devon flagged. Tagline "Make your house a home" stands. FB page id 134086539948962 stands. (grep: "Client identity CORRECTED")
- 2026-05-16 — **Buzzfile is not a verification source.** A Buzzfile result that matched a similar business name + phone area code to "603 Coatings LLC" in NH was incorporated as ground truth and propagated through `project.md`, both HTML pages, and LESSONS for a full session before Devon caught it. Lesson: when the client's own live site (or a screenshot from Devon) shows a different city/area code, the live site wins. Buzzfile / OpenCorporates / similar aggregators are LEADS, not facts. (grep: "Buzzfile is not a verification source")

## Topic clusters

### Hosting decision
- **Pivoted from Vercel → Netlify** for commercial-use TOS + free built-in form handling (grep: "POC repo already linked to Vercel")

### Client / business identity
- **Mike, Howe Renovations, O'Fallon MO** (St. Louis metro), 636-697-2408 — full contact info CORRECTED 2026-05-16 (grep: "Client identity CORRECTED")
- **Existing site baseline** — `howerenovations.com` is a stock "WELCOME" template at the root URL, but `/home` has the real logo + tagline + phone. POC is an upgrade. (grep: "Mike's existing site `howerenovations.com` is a stock template")

### Research / verification hygiene
- **Buzzfile / OpenCorporates are leads, not facts** — propagating a Buzzfile name+phone match without client-side verification took a full session to unwind (grep: "Buzzfile is not a verification source")
