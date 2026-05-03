# Councilor

Church council roster tracker — single-page webapp with localStorage persistence.

## Quick Start

Open `index.html` in any browser. No build step, no server, no dependencies.

## Features

- **Year-by-year roster** — navigate council terms (June–May, displayed as 2024–2025)
- **3×3 seat grid** — click any seat to assign or change a member
- **Auto-rollover** — new years copy forward the prior year's members for manual adjustment
- **Term tracking** — per-seat consecutive years with color-coded warnings (green/yellow/orange/red)
- **Service history** — total years served, consecutive streak, and term-limit status per person
- **Officers display** — President, VP, Secretary, Treasurer per year (read-only)
- **JSON export/import** — backup and restore your data

## Data

All data is stored in `localStorage` under the key `councilor_data`. Export a JSON backup via the button in the app header. To reset, open DevTools → Application → Local Storage → delete `councilor_data`.

## Council Rules

From [gs-constitution.md](gs-constitution.md):
- 9 elected members, each serving 3-year terms
- Max 2 consecutive full terms (6 years), then must rotate off for at least 1 year
- Terms begin at the close of the annual meeting (~June)
- Officers serve 1-year terms, elected from within the council

## Tech

Single HTML file with embedded CSS and JavaScript. No frameworks, no build tools.
