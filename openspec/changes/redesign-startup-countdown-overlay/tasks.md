# Tasks

## 1. Shared Overlay Presentation

- [x] 1.1 Add shared countdown overlay markup and responsive styling in index.html, including a centered number-only panel, subdued background, and non-blocking scrim; verify in a browser at narrow and wide viewport sizes.

## 2. Mode Integration

- [x] 2.1 Connect the stopwatch startup countdown to the shared overlay using its existing deadline, with a brief blink between values and no change to the countdown duration; verify 10 through 1, Stop, Reset, and normal stopwatch start behavior in a browser.
- [x] 2.2 Connect the interval and Tabata startup countdowns to the shared overlay using their existing deadlines, keeping round status outside the number-only panel; verify both modes' countdown, Stop/Reset, and subsequent timer progression in a browser.
- [x] 2.3 Preserve the existing countdown and session-start audio cues while adding the blink; verify cues remain synchronized to 3, 2, 1, and session start in all three modes.

## 3. Cross-Mode Verification

- [x] 3.1 Verify the overlay disappears when countdowns are cancelled or finish, controls remain usable while it is active, and the blink does not extend startup timing; run the project's available syntax checks and git diff --check.
