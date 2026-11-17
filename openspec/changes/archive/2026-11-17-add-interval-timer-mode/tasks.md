# Tasks

## 1. Timer-mode carousel

- [x] 1.1 Add stopwatch and interval mode selection with horizontal swipe and focused left/right keyboard navigation; expose the selected mode accessibly and prevent navigation during active timing or countdown. Verify swipes and arrow keys change modes only when allowed.
- [x] 1.2 Add the interval mode presentation using the shared timer page controls while retaining independent stopwatch and interval state. Verify switching after stopping does not start or reset either timer.

## 2. Interval configuration

- [x] 2.1 Add interval duration and total-round fields to the cogwheel Settings dialog with one-minute/one-round initial values and validation for positive whole duration and round count. Verify valid settings apply and invalid, zero, fractional, and out-of-range values are rejected.

## 3. Interval timing

- [x] 3.1 Implement interval countdown, current-round display, immediate advancement, and final-round completion. Verify a short multi-round session advances each round and stops at zero after the configured total.
- [x] 3.2 Implement pause, resume, and reset for interval timing without losing remaining time or settings. Verify pause/resume retains the current round and reset clears progress and restores the configured duration.

## 4. Integration verification

- [x] 4.1 Verify the existing stopwatch start, stop, reset, and startup-countdown settings still work after mode selection is added.
- [x] 4.2 Verify carousel, timer display, controls, and Settings dialog remain visible and usable without horizontal overflow on desktop, mobile portrait, and mobile landscape viewports.
