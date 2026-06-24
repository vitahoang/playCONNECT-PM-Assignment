# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Self-contained HTML slide deck for a playCONNECT Product Manager take-home assignment. No build step, no dependencies, no package manager — everything is a single file.

## Previewing

```bash
python3 -m http.server 8765
# Open http://localhost:8765/playCONNECT-PM-Assignment.html
```

Use Playwright MCP to take screenshots for verification. Save all Playwright artifacts under `./playwright-mcp/`.

## File Overview

- `playCONNECT-PM-Assignment.html` — 12-slide presentation deck (the main deliverable)
- `design-options.html` — 3 design option previews (reference only, not the deliverable)
- `playCONNECT - Product Manager - Home assignment.pdf` — original assignment brief

## Slide Deck Architecture

The deck is a single HTML file with inline CSS and JS:

- **Navigation**: keyboard `←` `→` arrow keys + dot indicators at the bottom
- **Fonts**: Barlow Condensed (headings, 700/800 weight) + Plus Jakarta Sans (body) via Google Fonts
- **CSS variables**: `--accent: #F07320` (orange), `--navy: #111827`, `--bg: #FFFFFF`, `--bg-card: #FAFAFA`, `--glow: #FEF0E6`, `--muted: #6B7280`, `--border: #E5E7EB`
- **`.slide`**: `position: absolute; inset: 0; display: flex; flex-direction: column; padding: 44px 60px 76px`
- **Orange top stripe**: `.slide::before` with `height: 3px; background: var(--accent)`

## CSS Layout Notes

- All flex children that are also grid containers need `min-height: 0` to prevent overflow
- Slide 4 (Platform Alignment): 5-column card grid (`flex: 1; min-height: 0`) above a Campaign Engine banner (`flex-shrink: 0`)
- `grid-template-rows: 1fr` makes grid cells stretch to fill the row height; `auto` + `align-items: start` lets them shrink to content
