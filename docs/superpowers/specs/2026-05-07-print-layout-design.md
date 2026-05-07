# Print Layout

## Summary

Add a Print button to the app that opens a clean, print-optimized page showing the current year's roster (seats and officers) in compact table format.

## What prints

1. **Title:** `Church Council Roster`
2. **Year:** `2024-2025 (Jun 2024 - May 2025)`
3. **Cohort info:** `Cohorts: Seats 1-3 start <Y>, 4-6 start <Y+1>, 7-9 start <Y+2>`
4. **Seats table:** columns for `#`, `Name`, `Tenure` -- 9 rows, with vacancies shown as "Vacant"
5. **Officers table:** columns for `Office`, `Name`, `Tenure` -- 4 rows, with unfilled shown as "Not set"

## What does NOT print

- People database section
- Service History table
- Interactive UI (buttons, inputs, dropdowns)
- Background colors, shadows, seat status colors

## Implementation

- **Button:** Add a `<button onclick="printRoster()">Print</button>` in `.header-buttons` next to Export/Import JSON buttons
- **Function `printRoster()`:** Opens a new window via `window.open()`, writes clean print-optimized HTML, calls `.print()` on load, closes window on `afterprint`
- **CSS:** Uses `@page { margin: 15mm }` inline in the print window. No shadows, borders-only, monochrome.
- **Data reuse:** Calls existing helpers `getSeatLabel()`, `getOfficerLabel()`, `formatYear()`, `formatYearLong()`, `getCycleStart()`, `getPersonName()`, `getOfficerConsecutive()`

## Edge cases

- **No current year selected:** Print button hidden or disabled
- **No people in database:** Names show as "Unknown" (using existing `getPersonName()` behavior)
- **All vacancies:** Table still renders with all rows marked vacant

## Non-goals

- No markdown export (separate feature)
- No print-all-years mode
- No color/status indicators in print
