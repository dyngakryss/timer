# Proposal

## Why

The timer page currently has a plain background, so the existing Spånga handball logo is not visible while using the timers. Displaying it as a subtle watermark adds team identity without distracting from the timer readout or controls.

## What Changes

- Show the available Spånga handball logo as a subtle background watermark in Stopwatch, Intervals, and Tabata modes.
- Keep timer content readable and controls usable over the watermark at supported screen sizes.

## Capabilities

### New Capabilities

### Modified Capabilities
- `stopwatch`: Show the logo watermark behind the stopwatch interface.
- `interval-timer`: Show the logo watermark behind the interval timer interface.
- `tabata-timer`: Show the logo watermark behind the Tabata timer interface.

## Impact

- Updates the shared timer page in `index.html` to use the existing `spangahanboll.png` image asset as the background watermark for all timer modes.
- No dependencies or timer behavior changes.
