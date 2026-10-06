# Google Ads Auto-Report — Manus Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)
[![Made for Manus](https://img.shields.io/badge/Made%20for-MANUS-5E17EB.svg)](https://manus.im)
[![Google Ads](https://img.shields.io/badge/Google_Ads-Connector-blue.svg)](docs/google-ads-connector-ru.md)

A [Manus](https://manus.im) skill that audits your Google Ads search campaigns and returns a structured optimization report — **no CSV exports, no manual work**. The skill pulls data straight from your ad account via the native Google Ads connector, applies a 5-principle analysis methodology with a 10-pattern diagnosis catalog, and delivers a verdict: what to fix now (1–2 actions), what to postpone, what to watch.

> **Note:** the skill's working language is Russian (built for RU-speaking business owners). This repo's documentation is in English for GitHub discoverability.

## Table of Contents

- [Who is this for](#who-is-this-for)
- [Installation](#installation)
- [Usage](#usage)
- [What you get](#what-you-get)
- [How it works](#how-it-works)
- [Repository structure](#repository-structure)
- [Requirements](#requirements)
- [FAQ](#faq)
- [License](#license)

## Who is this for

Business owners who run their own Google Ads and are tired of the Monday reporting routine: same tables, same numbers, same conclusions. Instead of spending an hour assembling reports, you connect the skill once — and get an analyst-grade verdict in minutes.

## Installation

Two steps, all inside Manus (~1 minute + one-time account connection):

1. **Install the skill.** Open in Manus (or Manus → Settings → Skills → Import from GitHub):
   `https://manus.im/import-skills?githubUrl=https%3A%2F%2Fgithub.com%2FIevgen-bot%2Fmanus-google-ads-otchet`
   Confirm the import (~10–30 seconds).
2. **Connect your ad account.** Manus → Add connectors → **Google Ads (Beta)** → Connect → sign in with the Google account that owns the ad account. Step-by-step: [docs/google-ads-connector-ru.md](docs/google-ads-connector-ru.md) (in Russian).

## Usage

In any Manus chat, run:

```
/google-ads-otchet make a report for the last 30 days
```

The skill will:
1. Pull data from your connected Google Ads account (campaigns, keywords, devices, geo, day of week, hour of day, audiences, demographics, ads) — last 30 days + previous 30 for trend context.
2. Ask two short questions if needed (your niche, your acceptable cost per lead) — or work with a stated caveat.
3. Return a structured 8-block report as a single file: context → data readiness → key observations → cross-report patterns → **actions for now (max 2)** → deferred → watch list → check-in schedule.

## What you get

- **Signal, not noise.** Segments with negligible spend/conversions are filtered out as noise (materiality principle) — you only see what moves your bottom line.
- **No made-up benchmarks.** Every metric is judged against your own account averages and your own target numbers — never against generic "industry standards".
- **Diagnosis before prescription.** Deviations are matched against a catalog of 10 diagnostic patterns (ad/segment mismatch, auction overheat, landing mismatch, pure waste, undertapped performer, budget/rank caps…) before any action is recommended.
- **Safe by design.** Max 2 actions per cycle, 20%-per-step cap on numeric changes, one-variable rule, hard scope limits (search campaigns only; no ad copywriting, no keyword suggestions, no account restructuring).

## How it works

The skill follows a fixed protocol (`skills/google-ads-otchet/SKILL.md`):

1. **Connector check** — Google Ads connector must be linked.
2. **Intake** — niche + acceptable CPL/CPA (2 questions, skippable with caveat).
3. **Data pull** — via the connector, 30+30 days, 9 report slices (`references/data-queries.md`).
4. **Readiness check** — ready / partial / deferred per slice.
5. **Analysis** — 5 methodological principles (`references/principles.md`).
6. **Pattern matching** — 10-pattern diagnosis catalog (`references/diagnosis-catalog.md`).
7. **Cross-slice synthesis** — device × hour, geo × device, keyword × geo, etc. (materiality + reinforcement + stability filters).
8. **Pareto selection** — rank by monetary weight, max 2 actions now, rest deferred; safety checks (`references/restrictions.md`).
9. **Report** — 8-block template (`references/report-template.md`).

## Repository structure

```
manus-google-ads-otchet/
├── README.md
├── LICENSE                      # MIT
├── SKILL.md                      # skill playbook (Russian) — must be at repo root for Manus import
├── references/                   # methodology (Russian)
│   ├── principles.md             # 5 analysis principles
│   ├── diagnosis-catalog.md      # 10 diagnostic patterns
│   ├── restrictions.md           # hard scope limits
│   ├── data-queries.md           # what to pull via the connector
│   └── report-template.md        # 8-block report structure
├── docs/
│   └── google-ads-connector-ru.md # connector setup guide (Russian)
├── .gitignore
└── PUBLISHING.md                 # repo setup checklist (description, topics)
```

## Requirements

- A Manus account (the Google Ads connector is currently in Beta and rolling out gradually). New to Manus? Register here: https://manus.im/share/6V79Hl9i0uWXYR87cT5AHJ
- Google Ads account access (owner or admin of the ad account).
- Search campaigns — Performance Max, Demand Gen, YouTube, Shopping and Discovery are out of scope by design.

## FAQ

**Do I need to export CSVs from Google Ads?**
No. The skill pulls everything itself through the native Google Ads connector. That's the whole point.

**I don't see the Google Ads connector in Manus.**
It's in Beta and rolling out gradually. If it's missing for you, wait for the rollout — the skill will pick it up as soon as the connector appears.

**Which language does the report come in?**
Russian. The skill is built for RU-speaking business owners.

**Can it rewrite my ads or suggest keywords?**
No — deliberately. The protocol forbids ad copywriting, keyword suggestions, site audits and account restructuring. It diagnoses and prescribes within a tight, safe scope.

**Is my ad account data sent anywhere?**
The skill runs inside your Manus session and reads your account through the connector you authorized. This repo contains only the skill's instructions — no data, no credentials.

## License

MIT — free to use, modify and share. See [LICENSE](LICENSE).
