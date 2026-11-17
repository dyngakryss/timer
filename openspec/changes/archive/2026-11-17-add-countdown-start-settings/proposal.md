# Proposal

## Why

Users may want a short preparation period before the stopwatch begins measuring elapsed time. A configurable countdown lets them set that delay from the stopwatch page and see the remaining seconds before timing starts.

## What Changes

- Add a Settings control that opens a panel for configuring a non-negative whole number of countdown seconds; zero disables the countdown.
- When Start is activated from an idle stopwatch, show the configured remaining seconds and automatically begin stopwatch timing at 00:00 when the countdown ends.
- Let Stop cancel an active countdown and Reset cancel it and clear elapsed time. After a normal pause, Start resumes immediately without another countdown.
- Keep the selected countdown setting for the current page session only.

## Capabilities

### New Capabilities

### Modified Capabilities
- `stopwatch`: Extend timing controls with an optional startup countdown and add settings-panel configuration behavior.

## Impact

- Updates the standalone `index.html` UI and client-side timing state.
- No external dependencies or API changes.
