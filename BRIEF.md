# Brief: finish and deploy Khodor Ghalayini's portfolio site

Hand this whole folder to whichever coding agent/tool you're using (Cursor, GitHub Copilot, Replit Agent, v0, bolt.new, another Claude session, or a human dev). It's written to be tool-agnostic.

## What this is

A one-page static portfolio for Khodor Ghalayini, a Technical Project Manager / Electrical & Electronic Security Systems Engineer (CCTV/VMS, access control, ELV) relocating from Abu Dhabi to New Zealand under the Green List. The site exists to back up a live job search — it's linked from his CV, cover letters, and LinkedIn, so recruiters and hiring managers at companies like Beca, GHD, Mott MacDonald and Gallagher will actually click through to it.

`index.html` already contains a complete, working first draft. **The layout, styling, structure and copy voice are final — do not redesign them.** The remaining work is: (1) fill in placeholder content, (2) wire up two links, (3) deploy it.

## Design system (already implemented — reference only, don't change)

- Colors: navy `#1F3864` (brand/headers), orange `#C0521A` (accent — same palette used across his CV and cover letters, keep it consistent), plus supporting neutrals defined as CSS custom properties at the top of `index.html`. Full light + dark mode already implemented via `prefers-color-scheme`.
- Type: IBM Plex Sans (headings/body), IBM Plex Mono (labels, data, section numbers) — loaded from Google Fonts.
- Motif: styled like a technical drawing set — a title block header, numbered "sheets" for each section, an equipment-schedule-style table for the systems index. This is intentional and ties to his actual professional vocabulary (BOQs, equipment schedules, as-builts) — keep it.
- Fully responsive down to ~360px width. No JS framework, no build tooling, no dependencies beyond the Google Fonts stylesheet link.

## Task 1 — Fill in the placeholder content

Every editable spot is marked two ways: visible `[EDIT]` text in the copy, and a `data-field="..."` attribute on the element for easy scripted find/replace. Search the file for `[EDIT` to find all of them. They are:

- **Case Study 1 (Enterprise CCTV Platform Migration):** `cs1-situation`, `cs1-role`, `cs1-approach`, `cs1-outcome`, `cs1-lesson`
- **Case Study 2 (Multi-Site Security Programme):** `cs2-situation`, `cs2-role`, `cs2-approach`, `cs2-outcome`, `cs2-lesson`
- **Case Study 3 (Automated Vehicle Access Integration):** `cs3-situation`, `cs3-role`, `cs3-approach`, `cs3-outcome`, `cs3-lesson`
- **Systems & Fleet table:** `systems-network-scale`, `systems-elv-scale` (approximate scale figures)
- **Beyond the Day Job:** `repo1-name`, `repo1-desc`, `repo2-name`, `repo2-desc` (GitHub repos), `venture1-desc` (LEADGEND), `venture2-desc` (AI Powered Kit)
- **Links:** `data-field="github-url"` and `data-field="github-url-2"` (both currently `href="#"` — point them at his real GitHub profile), `data-field="cv-link"` (currently points to `./assets/Khodor_Ghalayini_CV.pdf`, which needs to actually exist — see Task 2)

If you (the agent) don't have Khodor's real project details, **don't invent specifics** — ask him for the real content for each field rather than fabricating client names, numbers, or outcomes. The example text currently in each field is a reasonable placeholder/starting draft, not something to leave in the published version.

**Content rule that must survive whatever gets filled in:** no real client names, site addresses, floor plans, network diagrams, or IP ranges — several of the underlying projects are government and police facilities in Abu Dhabi, so anything identifying goes no further than aggregate numbers and generalized descriptions of what was done. This is a hard constraint, not a style preference.

## Task 2 — Wire up assets

1. Create an `assets/` folder next to `index.html`.
2. Add `Khodor_Ghalayini_CV.pdf` to it (Khodor has this file already — get it from him).
3. Confirm the footer's "Download CV" button (`data-field="cv-link"`) resolves correctly once deployed.
4. Optional: add a small favicon (a simple "KG" monogram is fine) — not required, `index.html` doesn't currently reference one.

## Task 3 — Deploy to GitHub Pages (no custom domain yet)

No domain has been purchased yet, and none is needed to ship this — do not wait on a domain purchase to deploy. Ship it now on the free GitHub Pages URL; the custom domain is a separate, later step (Stage B below), not a blocker.

**Repo name matters here — use the special GitHub Pages "user site" name:**

1. Create a new **public** GitHub repo named exactly `khodor04.github.io` (must match the GitHub username exactly, including case). This specific name makes GitHub Pages serve it at the clean root URL `https://khodor04.github.io/` — any other repo name would instead serve at `https://khodor04.github.io/<repo-name>/`, with an extra path segment. Do not name it `khodor-portfolio` or similar.
2. Push this folder's contents to the repo's default branch (`main`), at the repo root — `index.html` should sit at the top level, not inside a subfolder. **Do not add a `CNAME` file at this stage** — there's no domain to point it at yet, and an empty/placeholder CNAME file can make GitHub show a false "misconfigured custom domain" warning.
3. In the repo, go to **Settings → Pages**. For a `<username>.github.io` repo this is often enabled automatically on first push; if not, set Source to "Deploy from a branch", branch `main`, folder `/ (root)`.
4. Confirm the site is live and loads correctly at `https://khodor04.github.io/` — check phone width, desktop width, and both light/dark mode.

### Stage B — later, only once a domain is purchased (not part of this task)

If/when Khodor buys a domain (he's currently considering khodorghalayini.com), come back and: add a `CNAME` file to the repo root containing just the domain name; set it under Settings → Pages → Custom domain; add four **A** records on the registrar's apex/root (`@`) pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`; add a **CNAME** record for `www` pointing to `khodor04.github.io`; wait for DNS to verify in Settings → Pages; then enable "Enforce HTTPS". Until this happens, `https://khodor04.github.io/` is the real, final link to use everywhere (CV, cover letters, LinkedIn) — it isn't a placeholder.

## Explicit non-goals

- No backend, no database, no contact form that submits anywhere (there's nowhere for it to go without adding a third-party service like Formspree — leave that out unless Khodor asks for it specifically).
- No analytics/tracking scripts unless Khodor asks for them.
- No redesign, no new sections, no different color/type system — the brief is to complete and ship this design, not reinterpret it.

## Definition of done

- All `[EDIT]` placeholders replaced with real, anonymized content (or explicitly confirmed with Khodor).
- Both GitHub links point to his real profile.
- CV download button resolves to a real PDF.
- Repo is named `khodor04.github.io` and the site is live at `https://khodor04.github.io/` over HTTPS, rendering correctly at both phone width and desktop, in both light and dark mode. (The custom domain is Stage B, later, and is not required for this task to be done.)
