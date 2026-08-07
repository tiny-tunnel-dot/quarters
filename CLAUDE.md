# quarters

## What this is
The dev arcade — Tony's project roster (vault / GitHub / local) rendered as a
retro CRT arcade page with stats, a commit heatmap, and a playable breakout game.

## Stack
Static, single self-contained `index.html`. No build step, no dependencies.
Pixel fonts (Press Start 2P, VT323) and the commit data are inlined.

## Hosting
GitHub Pages from main: https://tiny-tunnel-dot.github.io/quarters/
(repo is public; a push to main redeploys the page)

## Current state
Sunrised 2026-08-06. See the vault _index for always-current state:
~/ObsidianVault/03-projects/quarters/_index.md

## Refreshing the data
All numbers are a baked snapshot (marked with the as-of date on the page).
To re-tally: recompute LOC/commits per repo in ~/Developer (dedupe worktrees:
commish-next-steps=commish, RJ-Hauler-invites=RJ-Hauler), merged PRs via
`gh pr list --state merged` per tiny-tunnel-dot repo, commit dates -> the
DATA constant + REPOS array + the static numbers in index.html.

## Workflow
- Feature branches + PRs. Never push to `main`.
- Merge via the GitHub PR web UI or terminal, never GitHub Desktop.
