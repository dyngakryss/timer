# Proposal

## Why

The current text-labeled Settings button takes visual space in the stopwatch heading. Replacing it with a clearly identifiable cogwheel keeps Settings easy to reach while giving the timer a cleaner, more compact interface.

## What Changes

- Replace the visible “Settings” text button with a cogwheel icon button positioned at the top-right of the stopwatch panel.
- Preserve the existing Settings dialog behavior and provide an accessible name for the icon-only control.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `stopwatch`: Specify the icon-only Settings control, its top-right placement, and accessible identification.

## Impact

- Affects the stopwatch heading and Settings button styling/markup in `index.html`.
- No API, dependency, or settings-dialog behavior changes.
