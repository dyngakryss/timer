# Spec Delta

## MODIFIED Requirements

### Requirement: Configure startup countdown from Settings
The stopwatch SHALL provide a Settings panel where the user can set and apply a non-negative whole number of countdown seconds; the initial setting SHALL be zero, and the selected value SHALL remain in effect for the current page session. The Settings panel SHALL be opened from an icon-only cogwheel button at the top-right of the stopwatch heading, and the button SHALL have the accessible name “Settings”.

#### Scenario: Open and update countdown settings
- **WHEN** the user opens Settings, enters a valid whole number of seconds, and applies the setting
- **THEN** the setting is accepted for the next start and Settings can be closed to return to the stopwatch

#### Scenario: Reject invalid countdown settings
- **WHEN** the user attempts to apply an empty, negative, or fractional countdown value
- **THEN** the invalid value is not accepted and the user can correct it

#### Scenario: Identify and locate the Settings control
- **WHEN** the stopwatch page is displayed
- **THEN** the Settings control is a cogwheel icon button without visible text, is positioned at the top-right of the stopwatch heading, and is exposed with the accessible name “Settings”
