# Publishing the JioSignage site (GitHub Pages)

The site is a set of static files (no build step). GitHub Pages will host it for
free at a public URL, and **every future `git push` auto-updates the live link.**

A local git repo is already initialized and the site files are committed. You only
need to (1) create a GitHub repo, (2) push, (3) turn on Pages.

## One-time setup

### 1. Create an empty repo on GitHub
Go to https://github.com/new → name it e.g. **jiosignage** → **Public** →
do NOT add a README/.gitignore → **Create repository**.

(Or, if you have the GitHub CLI: `gh auth login` then
`gh repo create jiosignage --public --source=. --remote=origin --push` — this also
does the push in step 2.)

### 2. Push this repo
In this folder (`C:\Users\chinmay.jungade\Downloads\Claude`), run — replacing
`YOUR-USERNAME`:

```bash
git remote add origin https://github.com/YOUR-USERNAME/jiosignage.git
git branch -M main
git push -u origin main
```

### 3. Enable GitHub Pages
On the repo page: **Settings → Pages → Build and deployment →
Source: "Deploy from a branch" → Branch: `main` / `/root` → Save.**

Wait ~1 minute. Your public link will be:

```
https://YOUR-USERNAME.github.io/jiosignage/
```

Share that link with your team.

## Updating the live site later (auto-updates)

Whenever you (or Claude) change any file, just run:

```bash
git add -A
git commit -m "describe the change"
git push
```

GitHub Pages redeploys automatically in ~30–60s — the shared link always shows
the latest version. No re-sharing needed.

## What gets published
Only these are tracked (see `.gitignore`): `index.html`, `jiosignage-landing.html`,
`features.html`, `login.html`, and the `images/` folder. Private/unrelated items
(`.claude/`, `JioSafetyShield-Parent/`, `JioSignage.html`, `MD/`) are **excluded**.

## Add the pending images
Before/after publishing, drop these in so the cards/dashboard show real photos:
- `images/industries/` → retail.jpg, qsr.jpg, hospitality.jpg, healthcare.jpg,
  corporate.jpg, education.jpg, manufacturing.jpg, banking.jpg, government.jpg,
  airports.jpg, smart-cities.jpg, kiosks-malls.jpg
- `images/dashboard.png` → the CMS dashboard screenshot
Then `git add -A && git commit -m "add images" && git push`.
