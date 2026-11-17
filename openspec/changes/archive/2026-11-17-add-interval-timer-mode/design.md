# Design

## Context

The application is a single `index.html` page with inline HTML, CSS, and JavaScript. The stopwatch currently owns the display, controls, refresh interval, and settings dialog; there is no test framework or external dependency. See the proposal and capability deltas for the user-facing scope.

## Goals / Non-Goals

**Goals:**
- Add interval timing without changing the existing stopwatch timing behavior.
- Keep mode-specific configuration in the existing Settings dialog.
- Make timer-mode navigation operable by both swipe and keyboard.

**Non-Goals:**
- Add rest periods, persistent storage, external libraries, or additional timer modes.
- Add visible previous/next buttons; navigation uses the requested swipe and keyboard-arrow interactions.

## Decisions

- Keep the feature in `index.html` and reuse the existing display, controls, settings dialog, and refresh loop. The app is currently a single-file page, so introducing modules or a framework would add unnecessary structure.
- Keep stopwatch state and interval state separate, and render the selected mode through shared page elements. This avoids changing the established stopwatch behavior while allowing mode navigation after a timer is stopped.
- Model an interval session with its configured duration and round count, current round, remaining milliseconds, and active deadline. Derive remaining time from the deadline during refresh instead of decrementing a counter, which reduces timer drift and supports pause/resume.
- On round completion, advance the current round and set a new deadline immediately; on the final round, stop at zero. A reset returns the timer to the configured duration and clears round progress.
- Show the interval duration and round count in the existing cogwheel dialog when interval mode is selected. Apply validated settings to the next start so edits do not change a session already in progress.
- Handle horizontal pointer gestures on the mode carousel and left/right keys when that region has keyboard focus. Ignore gestures that are predominantly vertical and do not navigate while a countdown or timer is running. Keep the selected mode exposed to assistive technology.

## Risks / Trade-offs

- [A swipe can be mistaken for page interaction] → Require a deliberate horizontal movement threshold, ignore vertical gestures, and avoid treating gestures that begin on controls as navigation.
- [A single refresh loop can mishandle a round boundary if a refresh is delayed] → Compare the current time with the deadline and advance based on deadlines rather than assuming each refresh represents one tick.
- [Keyboard arrow handling can interfere with other controls] → Handle arrow keys only when the mode-navigation region has focus and do not intercept keys inside the Settings dialog or form fields.
