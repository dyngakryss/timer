# Proposal

## Why

The current startup countdown appears within the timer's normal readout, making it less prominent and harder to see at a distance. A dedicated, focused overlay will make the preparation countdown clear across all timer modes without changing its duration or the existing start cues.

## What Changes

- Replace the in-layout display of the 10-second startup countdown with a centered overlay panel above the current timer interface.
- Show only the remaining whole-second number from 10 through 1 in the panel, using large, bold typography.
- Briefly hide or fade out each number between seconds to create a blink before showing the next number.
- Subdue the surrounding interface while the countdown is active, without preventing the user from cancelling or resetting the countdown.
- Preserve the fixed countdown duration, timer behavior, and existing audible countdown and session-start cues.

## Capabilities

### New Capabilities

### Modified Capabilities
- `stopwatch`: Present its fixed startup countdown in a blinking overlay instead of the normal timer readout.
- `interval-timer`: Present its fixed startup countdown in a blinking overlay instead of the normal timer readout.
- `tabata-timer`: Present its fixed startup countdown in a blinking overlay instead of the normal timer readout.

## Impact

- Updates the standalone `index.html` overlay markup, styles, and countdown presentation across all timer modes.
- No dependencies or API changes.
