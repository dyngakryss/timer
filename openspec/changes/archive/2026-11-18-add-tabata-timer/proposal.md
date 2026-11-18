# Proposal

## Why

The timer page supports a stopwatch and continuous interval rounds, but not a work/rest training cycle. A Tabata timer will let users configure work periods, recovery periods, rounds, and a startup countdown while using the existing timer-mode carousel and full-screen timer presentation.

## What Changes

- Add Tabata as a third timer mode, navigable alongside Stopwatch and Intervals.
- Provide Tabata Settings for work duration, rest duration, total rounds, and startup countdown.
- Run each round as a work countdown followed immediately by a rest countdown, including rest after the final work period, then complete.
- Support the same start, stop, reset, and round-status experience as the existing interval timer.

## Capabilities

### New Capabilities

- `tabata-timer`: Configure and run a sequence of work and rest periods with rounds and an optional startup countdown.

### Modified Capabilities

- `timer-mode-navigation`: Add Tabata to the ordered timer carousel and preserve navigation restrictions while any selected timer is running or counting down.

## Impact

- Affects the timer-mode carousel, settings dialog, timer state/rendering, and controls in `index.html`.
- Adds the `tabata-timer` specification and updates the timer-mode-navigation specification.
- No dependencies or external interfaces change.

## Assumptions

- Work and rest durations use the existing interval `MM:SS` format and must be positive.
- Defaults follow a common Tabata preset: 20 seconds work, 10 seconds rest, 8 rounds; startup countdown defaults to zero.
- Startup countdown is configured in whole seconds, starts once before the first work period, and does not repeat between rounds.
- Rest runs after every work period, including the final round, as confirmed by the user.
- Timer modes remain ordered Stopwatch, Intervals, Tabata, with no wraparound at either end of the carousel.
