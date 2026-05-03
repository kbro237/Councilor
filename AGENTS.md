# AGENTS.md — Councilor

Single-file client-side webapp for tracking church council rosters.  
Open `index.html` directly in a browser — no build, no server, no dependencies.

## Stack
- One HTML file with embedded CSS/JS. No framework, no bundler, no npm.
- Data persists in `localStorage` under key `councilor_data`.
- `gs-constitution.md` is a reference document (council rules), *not* parsed by the app.

## Data model (`localStorage`)
```json
{
  "version": 1,
  "people": [{ "id": "uuid", "name": "Name" }],
  "roster": {
    "2024": {
      "members": ["id", null, "id", ...9 slots],
      "officers": { "president": null, "vicePresident": null, "secretary": null, "treasurer": null }
    }
  }
}
```
- Year keys are integers (start of June–May term). Displayed as `2024–2025`.
- `members` array is always length 9 (seat positions 0–8). `null` = vacant.
- Officers per year exist in the data structure but the UI is read-only.

## Council rules (from constitution)
- 9 elected members, each serving **3-year terms** (staggered, ~3 rotate per year).
- **Max 2 consecutive full terms** (6 years). After that must rotate off at least 1 year.
- Terms begin at the close of the annual meeting (~June).

## UI conventions
- No pastor/pastor tracking — the user explicitly asked for this to be removed.
- Seat status colors: green (yr 1–3), yellow (yr 4–5), orange (yr 6), red (yr 7+).
- "Consecutive years" in a seat counts backward from current year within the same seat position.
- Service history "current streak" only considers consecutive years up to the latest year.
- Auto-rollover on new year creation copies all members from the prior year; the user adjusts manually.

## Git conventions
- All commits include a co-author trailer for opencode, including the model used:
  ```
  Co-authored-by: opencode (deepseek-v4-pro) <opencode@anomalyco.com>
  ```

## Testing
- No test suite. Open `index.html` in a browser and exercise the UI.
- To reset app data: open DevTools → Application → Local Storage → delete `councilor_data`.
