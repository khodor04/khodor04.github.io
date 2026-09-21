# khodor04.github.io — portfolio site

Static, single-page portfolio for Khodor Ghalayini (Technical Project Manager / Electrical & Electronic Security Systems Engineer), built to support an active New Zealand job search.

No custom domain yet — this deploys to the free `https://khodor04.github.io/` URL, which is the real link to use in applications for now. A domain can be added later without rebuilding anything (see Stage B in `BRIEF.md`).

## What's in this folder

- `index.html` — the entire site. No build step, no framework, no backend. Fonts load from Google Fonts (IBM Plex Sans / IBM Plex Mono); everything else is inline HTML/CSS/JS in this one file.
- `BRIEF.md` — the task brief for whoever (or whichever AI coding tool) finishes and deploys this. Read this first if you're picking up the work.
- `assets/` — put `Khodor_Ghalayini_CV.pdf` here (referenced by the "Download CV" button in the footer). This folder doesn't exist yet — create it and add the file.

## Preview locally

No build step needed — just open `index.html` directly in a browser, or serve it:

```bash
npx serve .
# or
python3 -m http.server 8000
```

## Deploy (GitHub Pages)

See "Task 3" in `BRIEF.md` — repo must be named exactly `khodor04.github.io` for the clean root URL. Custom domain setup (Stage B in the same file) is a later, optional step once a domain is purchased.
