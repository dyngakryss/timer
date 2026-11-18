# timer-settings-dialog Specification

## Purpose

Defines shared behavior for the timer settings dialog so users can dismiss it intentionally without losing access when interacting with its content.

## Requirements

### Requirement: Dismiss settings only when clicking outside the dialog
The timer settings dialog SHALL close on a click in the backdrop outside the dialog's visible bounds and SHALL remain open when the user clicks within the dialog, including its padding.

#### Scenario: Click the dialog backdrop
- **WHEN** the user clicks outside the settings dialog's visible bounds while it is open
- **THEN** the settings dialog closes

#### Scenario: Click dialog content or padding
- **WHEN** the user clicks within the settings dialog's visible bounds, including its padding
- **THEN** the settings dialog remains open
