# Proposal

## Why

The page currently offers only a stopwatch, so users cannot run repeated fixed-duration rounds or switch between timer types. An interval mode will support round-based countdowns while keeping the existing stopwatch available in the same page.

## What Changes

- Add an interval timer with a configurable round duration in minutes and seconds and a configurable total number of rounds.
- Count down each round, display the current round as it advances, automatically begin the next round without a rest period, and stop after the configured final round.
- Put interval configuration in the existing cogwheel Settings panel.
- Add horizontal swipe navigation between the stopwatch and interval timer, with keyboard arrow-key navigation when switching is allowed.
- Prevent switching timer modes while a timer is running or counting down; users can switch after stopping or completing it.
- Preserve existing stopwatch behavior and settings.

## Capabilities

### New Capabilities

- `interval-timer`: Configure and run a fixed-duration countdown across a finite number of rounds.
- `timer-mode-navigation`: Navigate between the stopwatch and interval timer using a horizontal carousel.

### Modified Capabilities

None.

## Impact

- Affects the timer display, heading/mode selection, settings dialog, controls, and inline timer logic in `index.html`.
- No external APIs or dependencies are required.
- There are currently no matching automated test files; implementation verification should cover timer behavior, keyboard/swipe navigation, settings validation, and responsive layouts.

## Assumptions

- A new interval timer starts with a one-minute round duration and one round; both are editable in Settings.
- Each round begins immediately after the previous round completes, with no rest interval.
- The displayed lap is the current round out of the configured total, beginning at 1 when timing starts.
- Stopping pauses the current round; resetting clears the lap progress and restores the configured round duration.
