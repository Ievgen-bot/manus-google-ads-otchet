# Publishing checklist — manus-google-ads-otchet

Everything the repo needs to be public, compliant and discoverable on GitHub. Do it once, in this order.

## 1. Create the repository

- Go to https://github.com/new
- **Name:** `manus-google-ads-otchet` (exact — the name itself carries search keywords)
- **Description** (copy-paste):
  `Manus skill that auto-audits Google Ads search campaigns and returns a structured optimization report — no CSV exports, data pulled via the native Google Ads connector`
- **Visibility:** Public
- **Do NOT** tick "Add a README file" / ".gitignore" / "license" — they are already in the bundle.
- Create.

## 2. Upload the files

Easiest (no terminal): on the new repo page → **uploading an existing file** → drag in the whole `repo/` folder contents (or the zip below) → Commit directly to `main`.

Alternative (terminal):
```bash
cd manus-google-ads-otchet
git init -b main
git add .
git commit -m "google-ads-otchet skill v1.0"
git remote add origin git@github.com:<your-username>/manus-google-ads-otchet.git
git push -u origin main
```

## 3. Set topics (repo page → ⚙️ About → Topics)

Copy-paste, one per line:
```
manus
manus-skill
google-ads
google-ads-api
ppc
ppc-audit
marketing-automation
ai-agents
report-automation
```

## 4. Finalize the README link

In `README.md`, replace `Ievgen-bot` in the import URL with your GitHub username/org, commit. The one-click install link then works:
`https://manus.im/import-skills?githubUrl=https%3A%2F%2Fgithub.com%2F<you>%2Fmanus-google-ads-otchet%2Ftree%2Fmain%2Fskills%2Fgoogle-ads-otchet`

## 5. Sanity checks

- [ ] README renders (badges visible, TOC links work)
- [ ] LICENSE shows as "MIT" in the repo header
- [ ] Repo is found via GitHub search for "manus google ads skill"
- [ ] Import link opens Manus skill import with `google-ads-otchet` prefilled

## Optional (later)

- **Social preview** (repo → Settings → Social preview, 1280×640): generate a banner in brand style.
- **Releases:** tag `v1.0` when the skill passes the manual test on a real ad account.
- **Discussions:** enable for user questions.
