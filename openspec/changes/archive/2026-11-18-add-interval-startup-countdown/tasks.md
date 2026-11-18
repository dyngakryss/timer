# Tasks

## 1. Interval Countdown Settings

- [x] 1.1 Add an interval-specific startup countdown setting and a seconds input in Interval Settings, default it to zero, and verify it appears only for Interval mode and accepts valid whole-number values.
- [x] 1.2 Apply and validate the interval countdown setting without changing stopwatch settings; verify invalid empty, negative, and fractional values are rejected and a valid value is retained for the page session.

## 2. Interval Startup Countdown Lifecycle

- [x] 2.1 Add interval countdown phase and deadline handling; verify a positive setting displays the countdown and starts round 1 at its full configured duration when it expires, while zero starts round 1 immediately.
- [x] 2.2 Handle Stop and Reset during startup countdown and preserve existing round pause/resume behavior; verify Stop and Reset cancel the countdown, Reset preserves settings, and resuming a paused round does not repeat the countdown.
- [x] 2.3 Include startup countdown in active controls and mode-switch guards; verify Stop is available and timer mode cannot change until the countdown is cancelled or completes.

## 3. Integration Verification

- [x] 3.1 Browser-test startup countdown, first-round start, round progression, completion, cancellation, reset, and pause/resume in both zero and positive countdown configurations; verify existing stopwatch behavior remains unchanged.
