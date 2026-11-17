# Tasks

## 1. Full-Screen Timer Layout

- [x] 1.1 Update the shared timer layout and clock sizing in `index.html` to remove the outer card treatment and use the available viewport for both modes; verify stopwatch and interval controls remain visible, usable, and free of horizontal overflow on mobile and tablet portrait and landscape viewports.

## 2. Interval Round Presentation

- [x] 2.1 Place the current interval round number to the left of the countdown at matching type size while retaining current/total round information accessibly; verify the number updates on round advances and remains correct after pause, resume, reset, and final completion.

## 3. Interval Duration Settings

- [x] 3.1 Replace separate minute and second settings with a single “Round duration (mm:ss)” text field and parse/validate its value; verify valid values apply to the next session and malformed, zero, or out-of-range values are rejected with a correctable error.

## 4. Mode Navigation Copy

- [x] 4.1 Remove the visible carousel instruction and “Timer X of 2” text without losing accessible mode identification; verify swipe and focused-arrow navigation still work when allowed and mode changes remain blocked while timing is active.
