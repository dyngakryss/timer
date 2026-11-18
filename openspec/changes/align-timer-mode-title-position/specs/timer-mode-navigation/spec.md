# Spec Delta

## ADDED Requirements

### Requirement: Present timer mode titles in a consistent heading position
The timer page SHALL render the selected mode title in the same heading-row position across Stopwatch, Intervals, and Tabata. The title SHALL remain visually aligned when a mode does or does not show the settings control.

#### Scenario: Switch from stopwatch to a settings-enabled mode
- **WHEN** the user switches from Stopwatch to Intervals or Tabata
- **THEN** the mode title remains in the same heading position while the settings control appears at the right

#### Scenario: Switch from a settings-enabled mode to stopwatch
- **WHEN** the user switches from Intervals or Tabata to Stopwatch
- **THEN** the mode title remains in the same heading position while the settings control remains hidden
