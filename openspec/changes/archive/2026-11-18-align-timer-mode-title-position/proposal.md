# Proposal

## Why

The timer mode title moves vertically because the stopwatch heading has no settings button while Interval and Tabata reserve one. This makes STOPWATCH, INTERVALS, and TABATA appear in inconsistent positions when switching modes.

## What Changes

- Keep the timer mode title in one fixed heading-row position across Stopwatch, Intervals, and Tabata.
- Preserve the existing right-aligned settings control only for modes that support settings.
- Make the heading layout remain consistent across responsive viewport sizes.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `timer-mode-navigation`: Add a stable presentation requirement for the selected timer mode title while switching between modes.

## Impact

- Affects the heading layout in `index.html`.
- No timer behavior, navigation rules, settings behavior, APIs, or dependencies change.
