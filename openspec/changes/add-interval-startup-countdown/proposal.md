# Proposal

## Why

The stopwatch supports a configurable pre-start countdown, but interval sessions begin immediately. Adding the same setup option to Interval Settings lets users prepare before the first round without changing round timing or progression.

## What Changes

- Add a non-negative whole-number startup countdown setting to the interval Settings panel, using the same seconds-based configuration and validation as the stopwatch.
- For a new interval session, count down before starting round 1 when the configured value is greater than zero; a zero value starts the first round immediately.
- Make Stop and Reset cancel an in-progress interval startup countdown, and ensure resuming a paused round does not repeat the startup countdown.
- Keep the countdown setting for the current page session and apply changes to the next interval session.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `interval-timer`: Add startup countdown configuration and define how it interacts with interval session start, cancellation, pause/resume, and reset.

## Impact

- Affects the interval Settings panel and interval timing state/rendering in `index.html`.
- No dependencies or external interfaces change.

## Assumptions

- The countdown runs once before round 1 of a new interval session, not before each round.
- Stopping during the countdown cancels it and leaves the interval session unstarted; the next Start begins a fresh countdown.
- Reset during the countdown cancels it and retains the configured countdown, matching stopwatch behavior.
- Startup countdown is not repeated when resuming a paused interval round.
