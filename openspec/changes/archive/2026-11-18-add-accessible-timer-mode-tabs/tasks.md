# Tasks

## 1. Page semantics and mode context

- [x] 1.1 Update `index.html` to preserve one native main landmark, group the active timer in a mode-labeled section, and update the document title on mode changes; verify assistive technology exposes exactly one main landmark and the title matches Stopwatch, Intervals, and Tabata as each is selected.

## 2. Accessible mode tabs

- [x] 2.1 Add the visible tablist and tabs with selected state, non-wrapping arrow-key focus and selection, pointer activation, and disabled state matching the existing mode-switch guard; verify keyboard-only and mouse/touch-only mode changes, arrow and swipe shortcuts, selected state, and blocked changes during active timers and startup countdowns.
- [x] 2.2 Style the tabs within the existing layout and compact landscape breakpoint; verify all tabs and timer controls remain visible and usable in a small-height landscape viewport.
- [x] 2.3 Hide the duplicate visible mode heading while preserving the accessible section heading; verify the active tab and accessible heading identify the mode without another visible mode label.

## 3. Settings dialog backdrop

- [x] 3.1 Use dialog bounds to distinguish backdrop clicks from clicks inside the dialog; verify backdrop clicks close Settings while clicks on dialog content and padding leave it open.
