# Design

## Context

The standalone timer page shares one interface across stopwatch, interval, and Tabata modes. Each mode maintains its own startup-countdown deadline and updates the normal timer readout while that countdown is active. See proposal.md and specs/ for the motivation and behavior contract.

## Goals / Non-Goals

**Goals:**
- Present the same countdown overlay consistently in all three modes without changing timer deadlines or sound cues.
- Keep the panel readable across small and large viewports.
- Preserve access to existing timer controls while the countdown is visible.

**Non-Goals:**
- Change the 10-second countdown, round progress, or timing behavior.
- Add animations or overlays during normal stopwatch, interval, or Tabata timing.
- Add settings or external dependencies.

## Decisions

- Use one shared overlay element for all modes, positioned over the existing interface and centered in the viewport. A dark translucent scrim will dim the surrounding interface while active; large, bold, tabular-number typography will emphasize the remaining whole seconds from 10 through 1.
- Keep the panel's content to the countdown number only. Leave existing interval/Tabata round status and timer controls in the underlying interface, subdued but visible; make the visual scrim non-blocking so Stop and Reset remain usable.
- Derive the number from each mode's existing deadline rather than a new decrementing counter. Briefly fade or hide the current number for approximately 150 ms at each second transition, then show the next number. The blink must not extend the 10-second deadline; cue timing remains tied to the same countdown values and session-start transition.
- Keep the existing timer readout's accessible countdown semantics and treat the overlay as a visual presentation layer so assistive technology does not announce a duplicate countdown.

## Risks / Trade-offs

- The scrim may reduce contrast for the underlying controls → keep controls visible and operable, with dimming limited to the active countdown.
- A blink can briefly leave the panel without a visible number → limit the blank/fade phase to approximately 150 ms and derive it from the countdown deadline.
- Large text may not fit every viewport → use responsive sizing and tabular digits so the 10-to-1 sequence remains centered and legible.

## Migration Plan

No persisted data or external APIs are involved. Add the overlay presentation and retain the existing countdown state, controls, and sounds. Rolling back removes the overlay while preserving the existing in-readout countdown behavior.
