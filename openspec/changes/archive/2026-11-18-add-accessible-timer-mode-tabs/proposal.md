# Proposal

## Why

Timer modes are currently discoverable only through swiping or focused arrow-key navigation, leaving no visible way to choose a mode and no reliable pointer-only alternative. The page also overrides its main landmark with carousel semantics, keeps a stale document title, and dismisses settings when dialog padding is clicked.

## What Changes

- Add visible Stopwatch, Intervals, and Tabata tabs with tablist semantics and selected state; disable mode changes while the current timer is active, while retaining swipe and arrow-key shortcuts. Use the selected tab as the sole visible mode label.
- Restore the page's main landmark, structure timer content in appropriate sections, retain an accessible mode heading, and update the document title whenever the selected mode changes.
- Dismiss Settings on clicks outside its dialog bounds, not clicks on padding inside the dialog.
- Keep the page static and dependency-free, preserve existing timer controls, and fit the tabs in the small-height landscape layout without broader visual redesign.

## Capabilities

### New Capabilities
- `timer-settings-dialog`: Define backdrop-click dismissal behavior for the shared timer settings dialog.

### Modified Capabilities
- `timer-mode-navigation`: Add visible accessible tabs, retain swipe and arrow navigation, and specify page landmark and mode-title semantics.

## Impact

- Updates the shared page in `index.html`; no dependencies, timer logic, or sound behavior change.
- Adds a shared settings-dialog behavior specification and updates the timer-mode-navigation specification.
