# STATUS - free-focus-tools-directory

Date: 2026-11-05

## What was built

A static, offline, single-file directory of **34 free focus and ADHD-help tools**, organized into seven categories:

| Category | Cards |
| --- | --- |
| Distraction blockers | SelfControl, LeechBlock NG, StayFocusd, Cold Turkey Blocker (free), Screen Time (iOS), Digital Wellbeing (Android) |
| Pomodoro and gentle timers | Pomofocus, Pomodor, TomatoTimer, Stretchly, Focus sessions (Windows 11), the humble iPhone timer |
| Body doubling and coworking | Focusmate, LifeAt, Google Meet do-it-together sessions |
| Text to speech | Edge Read Aloud, Balabolka, NaturalReader (free tier), TTSMaker |
| Note capture and brain dumps | Joplin, Obsidian, OneNote, Google Keep, Simplenote |
| Soundscapes and focus sounds | myNoise, Rainy Mood, Coffitivity, Noisli (free plan) |
| Browser calm-downs | uBlock Origin, Firefox Reader View, Immersive Reader (Edge), Just Read, Momentum, Chrome tab groups |

Every card states: what it does, why it is genuinely free (with honest limits - freemium caps, platform gaps, voice quality), the official free source (1-3 links, restricted to each tool's official domains only), a beginner verdict (Start here / Easy win / Worth practicing), and per-card `lastChecked` / `recheckBy` dates (all 2026-11-05 / 2027-02-05).

Need-based filters: **procrastination (17 cards), overwhelm (28), study (29), chores (8)**, plus device/browser filter and full-text search.

Architecture matches the sibling `free-accessibility-tools-directory`: JSON-driven (`data/tools.json`), template + build script inline everything into one `index.html` (138 KB) that works offline from a double-click, with static (no-JS) cards baked in. No dependencies, no network in build or test, no affiliate links, no secrets, no personal data.

## How to run it

- **Use it**: open `index.html` in any browser. Fully offline.
- **Build**: `npm run build` (assembles `index.html` from `template.html`, `assets/`, `data/tools.json`).
- **Test**: `npm test` (56 checks; no dependencies needed; exit code 0 on success).
- **Maintain**: see `README.md` (field rules, quarterly recheck routine, commit `data/tools.json` + rebuilt `index.html` together).

## Verification results

- `npm run build` - PASS (built 138.3 KB single file, 34 cards, no unreplaced markers).
- `npm test` - **ALL PASS (56 passed, 0 failed)**:
  - Schema: all field/enums/dates/length rules, unique slugs, every category ≥ 2 cards, all four need filters ≥ 3 cards, meta credited to Asdale Dynamics, LLC, companion credit present, recheck dates not lapsed.
  - Logic: need/platform filters exact and monotonic, search + empty state, verdict-leading sort per category, complete card HTML for all 34 tools.
  - Built page: byte-identical to a fresh build, embedded JSON equals source, no external assets (true offline), all official URLs present in the page, no affiliate-style URL patterns, MIT + credit lines intact, disclaimers present, no secrets detected, size under 250 KB.
- All card URLs were fetched live during authoring (2026-11-05) and returned 200 (final URLs after redirects, e.g. Apple Screen Time support article 108806). LeechBlock's home was corrected to `proginosko.com/leechblock/` after the commonly-cited `leechblockng.com` did not resolve.

## Environment

- Node v20.19.2; no packages installed; `npm run build` and `npm test` run clean.

## Known gaps / planned next steps

1. **Recheck clock**: tests fail loudly after 2027-02-05 (the built-in quarterly pass). First maintenance recheck is due then; per-card freemium limits (Focusmate session count, Noisli streaming minutes, NaturalReader word limits) are the most likely things to drift.
2. **URL rot**: only card links were verified, not every deep translation of every tool's docs. If an official page restructures, update the card's URL and bump its dates.
3. **Coverage**: deliberate omissions include paid-with-free-trial tools (Freedom, Flow Club), app-store-hosted linkboards, and regional phone-maker wellbeing suites beyond stock Android; each would need its own verification pass. A future pass could add ~2-4 cards (e.g. a visual-timer card, an accountability-reminder card) without schema changes.
4. **No browser smoke test**: rendering logic is unit-tested in Node, but there is no headless-browser test in this repo (kept dependency-free by design). Opening `index.html` once per release in a real browser is the remaining manual check.
5. The JavaScript-off fallback lists cards but filters/search need JS (expected; stated in a noscript note on the page).

## License and credit

MIT - Copyright (c) 2026 Asdale Dynamics, LLC. Built by Asdale Dynamics, LLC as part of Dylan Asdale's beginner-friendly AI education collection. Complements `free-accessibility-tools-directory`. Educational information only - not medical advice.
