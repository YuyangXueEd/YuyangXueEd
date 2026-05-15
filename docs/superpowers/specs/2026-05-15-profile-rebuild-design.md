# Profile Rebuild — Dashboard Showcase

**Date:** 2026-05-15
**Owner:** Yuyang Xue (YuyangXueEd)
**Goal:** Rebuild the GitHub profile README from a 2021-vintage placeholder into a dense, visually striking dashboard that surfaces the full research × builder × personal identity.

## Identity & Theme

- Identity: Hybrid (research × builder) with personal touch
- Density: Dense / showcase
- Language: English only
- Unified color theme across all SVG widgets: **tokyonight** (with `radical` as fallback if any widget lacks `tokyonight`)
- Brand color for capsule-render and accents: `#7AA2F7` (tokyonight blue)

## Page Structure (top → bottom)

### 1. Header banner
- `capsule-render` SVG: wave style, gradient (tokyonight palette), centered title "Yuyang Xue · 薛宇阳", subtitle "PostDoc @ The University of Edinburgh".
- Profile views counter (komarev) — small badge.
- Followers + stars-earned badges (shields.io).

### 2. Typing tagline
- `readme-typing-svg.demolab.com`, 3-line rotation:
  - `PostDoc working on Agents`
  - `Causality × Medical Imaging × Diffusion`
  - `Research × Engineering × Indie Games`
- Theme matched to tokyonight palette.

### 3. About
- Single short paragraph (3-4 lines). No bullet list, no emoji-heavy enumeration.
- Mentions: VIOS at Edinburgh, CHAI-UK affiliation, Guesswhat-Studio side org, blog https://rasin.cyou.

### 4. 🔭 Now
- Three bullets, hand-maintained:
  - Building agent systems for causal reasoning & education (EducAgent, CAUST). Recent submissions to top ML venues.
  - Maintaining Linnet — AI morning briefing from arXiv / HN / GitHub.
  - Co-developing PhenoAssistant — agent-assisted plant phenotyping at VIOS group.

### 5. 🛠 Tech stack
- Grid of `skillicons.dev` icons. Selection (in order):
  - python, pytorch, ts, astro, gdscript-equivalent (godot), latex, docker, kubernetes, linux, git, github, vscode

### 6. 📚 Featured Research (2×2 pin-card grid via HTML `<table>`)
- CRCE — BMVC 2025 (vios-s/CRCE)
- gmt-leaf-ins-seg — WACV 2025 (vios-s/gmt-leaf-ins-seg)
- CMRxRECON_Challenge_EDIPO — MICCAI (vios-s/CMRxRECON_Challenge_EDIPO)
- DOTS — Diffusion Ordered Temporal Structure (CHAI-UK/DOTS)
- Cards via `github-readme-stats/api/pin?...&theme=tokyonight`.

### 7. 🛠 Featured Projects (2×2 pin-card grid)
- Linnet — AI morning briefing (YuyangXueEd/Linnet)
- MuLTIHydra — Lightning + Hydra + Comet ML template (YuyangXueEd/MuLTIHydra)
- kubmonitor_cli — Kubernetes TUI job monitor (vios-s fork)
- VioScope — research clawbot for VIOS

### 8. 🎮 Off-the-clock
- Short paragraph: "When not in the lab, I make small 2D games with Godot under [Guesswhat-Studio](https://github.com/Guesswhat-Studio) and write notes at [rasin.cyou](https://rasin.cyou)."
- Two pin-cards: Guesswhat-Studio/Opsis, Guesswhat-Studio/Calabash.

### 9. 📊 Stats dashboard (the "showcase" part)
- Row 1: github-readme-stats (overall) + top-langs (side-by-side via `<table>`), both `tokyonight`.
- Row 2: github-readme-streak-stats (`tokyonight`).
- Row 3: github-readme-activity-graph (`tokyonight`) — animated-looking line chart.
- Row 4: Snake animation eating contributions (Platane/snk output) — full-width.
- Row 5: Existing rich metrics SVG (`github-metrics.svg`), now enriched with extra plugins.

### 10. Trophies & footer
- github-profile-trophy (`tokyonight`) — single row, 6 trophies.
- Wakatime stats card (kept from current README, retheme to tokyonight).
- Closing line: contact email + Google Scholar (`nWQX_0AAAAAJ`) + ORCID (`0000-0002-2281-9418`) + blog link.

## Workflow / automation changes

### A. Existing `Metrics` workflow — enrich plugins

Add these plugins to `.github/workflows/main.yml`:
- `plugin_topics: yes` + `plugin_topics_mode: starred` — surfaces interests
- `plugin_stargazers: yes` — stargazers chart over time
- `plugin_habits: yes` + `plugin_habits_facts: yes` + `plugin_habits_charts: yes`
- `plugin_followup: yes` — open/closed issues, PRs
- `plugin_lines: yes` — total lines added/removed (drops sections that load too slow can be removed later)

Keep all existing plugins. Don't change `template`/`base`.

### B. New `Snake` workflow — `.github/workflows/snake.yml`

- Runs daily on cron + on `push` to main + manual dispatch
- Uses `Platane/snk@v3`
- Outputs:
  - `github-contribution-grid-snake.svg` (light)
  - `github-contribution-grid-snake-dark.svg` (tokyonight palette)
- Pushes both to `output` branch
- README references via `https://raw.githubusercontent.com/YuyangXueEd/YuyangXueEd/output/...`

## YAGNI / explicit exclusions

- ❌ No timeline/narrative blocks (user explicitly said no timeline)
- ❌ No fork-only repos in Featured (STACE/EducAgent fork/MACE/RSSHub stay off the README)
- ❌ No private repos referenced (chai-cxr, MRIffusion, Foundation-Models, Yuyang_ED_Thesis, ICLR2026_UST, AgentStressTest_ICML2026)
- ❌ No Chinese subtitles in body content (header `薛宇阳` is the only CN — as personal touch)
- ❌ No Spotify/now-playing widget (user did not opt in; would require extra OAuth)
- ❌ No 3D contribution graph (visually duplicates snake + activity graph)

## Files touched

| File | Action |
|---|---|
| `README.md` | Full rewrite |
| `.github/workflows/main.yml` | Add plugin lines (no structural change) |
| `.github/workflows/snake.yml` | **New** |

## Success criteria

- README renders correctly on github.com/YuyangXueEd (rendered visually checked)
- All SVG URLs return 200 (validated manually post-merge)
- Metrics workflow still passes (existing token already has needed scopes)
- Snake workflow successfully creates `output` branch on first run
- All four orgs (vios-s, CHAI-UK, VIOS-Group, Guesswhat-Studio) reachable from the README
