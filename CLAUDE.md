# CLAUDE.md — SWOhell.com

## What This Is

A single-page dashboard tracking Allan & Charlie's NYC Stop Work Order situation at 176 Johnson St, Unit 6A, Brooklyn. Deployed at [swohell.com](http://swohell.com).

## Architecture

- **`index.html`** — Single HTML file with inline CSS and JS. Fetches `data.json` at load time and renders all sections.
- **`data.json`** — The "database." All content, dates, team info, blockers, timeline, etc. live here. Update this file to change what the site displays.
- **`banner.jpeg`** — Hero image at the top of the page.
- **`CNAME`** — Points to `swohell.com`.

## Deploy Flow

This site is deployed via **GitHub Pages** from the `main` branch of `HeyHolmes/swohell`.

**To publish changes:**
```bash
cd /Users/allanholmes/jallansbrain/projects/active/toy-factory-home/swohell-site
git add <files>
git commit -m "description of change"
git push origin main
```

Changes go live ~1 minute after push. GitHub Pages serves directly from the repo root.

**Critical:** Editing `data.json` locally is NOT enough. You MUST commit and push to make changes appear on the live site.

## data.json Structure

| Key | Purpose |
|-----|---------|
| `status` | Top banner headline, SWO date, next deadline |
| `nextAction` | Black card at top — the single most important thing to do |
| `keyDates` | Timeline of upcoming dates with countdowns |
| `penalties` | Financial obligations (paid, pending, unknown) |
| `rent` | Displacement cost tracking ($800/week) |
| `blockers` | Current blockers with severity (red/yellow/green/gray) |
| `timelineDone` | Completed events (chronological) |
| `timelineTodo` | Remaining steps to construction resuming |
| `team` | All people involved with roles and current status |
| `survivalGuide` | Flowchart, contacts, tips for other homeowners |
| `openQuestions` | Unanswered questions with severity |
| `intelLog` | Intel gathered from calls/emails |
| `legalRequirements` | NYC Admin Code sections relevant to SWO rescission |
| `displacementCost` | Running cost of not being able to move in |
| `property` | Address, BIN, violations, professionals |
| `footer` | Quote and credits |

## Known Issues

- **Obsidian sync can wipe `data.json`** — Obsidian treats it as a vault file and can overwrite it with empty content. Obsidian sync should be disabled for this folder, or the folder should be excluded from sync.
- **New data.json sections (openQuestions, intelLog, legalRequirements, displacementCost) are not yet rendered in index.html** — the data is there but the HTML/JS hasn't been updated to display them.

## Who Updates What

- **Claude Co-Work** monitors emails and prepares data updates, but cannot reliably write to disk. It should pass update instructions to Claude Code.
- **Claude Code** applies the edits to `data.json` and/or `index.html`, then commits and pushes.
- **Allan** may edit files directly or provide updates verbally.
