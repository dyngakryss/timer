# Proposal

## Why

The device can turn off its screen while a user is relying on an active timer, making the display difficult to monitor. Keeping the screen awake during timing lets users follow Stopwatch, Intervals, and Tabata without repeatedly touching the device.

## What Changes

- Keep the screen awake while any timer is actively counting, including its startup countdown.
- Release the screen wake lock when timing is paused, stopped, reset, or completed, and reacquire it if an active timer becomes visible again after the page was hidden.
- Continue timer operation if the browser or device does not support or grant a screen wake lock.

## Capabilities

### New Capabilities
- `screen-wake-lock`: Keep the display awake while a timer is active across all timer modes.

### Modified Capabilities

## Impact

- `index.html`: Integrate screen wake-lock lifecycle with the shared timer controls and visibility changes.
- Uses the browser Screen Wake Lock API where available; no new dependencies are expected.
