# Proposal

## Why

The large standalone round numeral competes visually with the interval countdown, while the useful “Round X of Y” context is currently placed below the clock. Making the round context a smaller label above the timer will clarify hierarchy and keep the countdown as the primary focus.

## What Changes

- Remove the large standalone round numeral beside the interval clock.
- Move the “Round X of Y” status above the countdown and size it to approximately 67% of the clock text.
- Preserve the round status updates for initial, advancing, paused, reset, and completed interval sessions.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `interval-timer`: Change the visual presentation and placement of current/total round information.

## Impact

- Affects the interval timer readout markup and styles in `index.html`.
- Does not change timer behavior, settings, or dependencies.

## Assumptions

- “33% smaller” means the round-status text uses 67% of the countdown’s computed font size.
- The “Round X of Y” line remains the round indicator, and the standalone large numeral is removed entirely.
