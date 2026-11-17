# Proposal

## Why

The timer page currently places both timer modes inside a bordered card and spends display space on carousel instructions and position text. The interval duration is also split across separate fields, while the current round number is visually secondary to the clock.

## What Changes

- Remove the visible carousel instruction and “Timer X of 2” position text while retaining accessible mode identification and swipe/keyboard navigation.
- Use a borderless, full-viewport layout for both timer modes and scale the timer display to use the available screen space while keeping controls usable.
- In interval mode, show the current round number in clock-sized type to the left of the countdown.
- Replace separate interval minute and second inputs with one text field labeled “Round duration (mm:ss)”, using and validating minutes:seconds formatting.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `stopwatch`: Update the responsive layout requirement for the full-screen, borderless timer presentation and larger clock.
- `interval-timer`: Update round display and duration configuration behavior.
- `timer-mode-navigation`: Remove visible instructional and carousel position copy while retaining accessible mode identification and keyboard navigation.

## Impact

- Affects the layout and timer display in `index.html`, plus interval Settings markup, parsing, and validation.
- No dependencies or external interfaces change.

## Assumptions

- “Round number” means the current round index that increments during an interval session; the total round count remains available as a secondary/accessibility description.
- The duration field accepts minutes and seconds separated by a colon, with seconds from `00` through `59`; minutes may contain one or more digits.
- The full-screen presentation removes the outer card border, rounded container, and shadow but retains the dark page background and existing controls.
