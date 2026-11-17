# stopwatch Specification

## Purpose

Provides a simple browser-based stopwatch so users can measure elapsed time and control timing from a standalone page.

## Requirements

### Requirement: Display elapsed minutes and seconds
The stopwatch SHALL display elapsed time as minutes and seconds, with seconds ranging from 00 to 59 and minutes increasing as time elapses.

#### Scenario: Initial display
- **WHEN** the stopwatch page is opened
- **THEN** the elapsed time is displayed as 00:00

#### Scenario: Elapsed time advances
- **WHEN** the stopwatch is running
- **THEN** the displayed seconds advance with elapsed time and roll over into the minutes without resetting the elapsed total

### Requirement: Control stopwatch timing
The stopwatch SHALL allow the user to start or resume timing, stop timing without clearing elapsed time, and reset elapsed time to zero. When a startup countdown is configured, Start from zero SHALL begin the countdown before stopwatch timing; Start after pausing SHALL resume immediately without another countdown.

#### Scenario: Start timing
- **WHEN** the user activates Start while the stopwatch is stopped and the configured countdown is zero
- **THEN** the stopwatch begins counting from its displayed elapsed time

#### Scenario: Stop and resume timing
- **WHEN** the user activates Stop while the stopwatch is running and later activates Start
- **THEN** the stopwatch pauses at its elapsed time and resumes from that time without counting the paused interval or repeating the startup countdown

#### Scenario: Reset timing
- **WHEN** the user activates Reset
- **THEN** the stopwatch stops and displays 00:00

### Requirement: Configure startup countdown from Settings
The stopwatch SHALL provide a Settings panel where the user can set and apply a non-negative whole number of countdown seconds; the initial setting SHALL be zero, and the selected value SHALL remain in effect for the current page session.

#### Scenario: Open and update countdown settings
- **WHEN** the user opens Settings, enters a valid whole number of seconds, and applies the setting
- **THEN** the setting is accepted for the next start and Settings can be closed to return to the stopwatch

#### Scenario: Reject invalid countdown settings
- **WHEN** the user attempts to apply an empty, negative, or fractional countdown value
- **THEN** the invalid value is not accepted and the user can correct it

### Requirement: Show countdown before stopwatch timing
When a countdown greater than zero is configured and the stopwatch is at zero, activating Start SHALL display the remaining time as minutes and seconds, then automatically begin stopwatch timing at 00:00 when the countdown reaches zero.

#### Scenario: Countdown reaches zero
- **WHEN** the user activates Start with a positive countdown configured
- **THEN** the timer display counts down the remaining time and the stopwatch automatically starts from 00:00 when the countdown completes

#### Scenario: Cancel countdown with Stop
- **WHEN** the user activates Stop during the startup countdown
- **THEN** the countdown is cancelled, the stopwatch remains stopped at 00:00, and Start is available to begin again

#### Scenario: Cancel countdown with Reset
- **WHEN** the user activates Reset during the startup countdown
- **THEN** the countdown is cancelled, the stopwatch remains stopped at 00:00, and the configured countdown setting remains available for the next start

### Requirement: Adapt the stopwatch layout to mobile and tablet viewports
The stopwatch page SHALL remain readable and fully usable on mobile phones and tablets in portrait and landscape orientations, without horizontal overflow or clipped timer controls.

#### Scenario: Mobile portrait layout
- **WHEN** the page is viewed on a mobile phone in portrait orientation
- **THEN** the timer remains readable and all controls fit within the viewport and can be activated

#### Scenario: Mobile landscape layout
- **WHEN** the page is viewed on a mobile phone in landscape orientation
- **THEN** the timer and all controls remain visible and usable within the viewport height and width

#### Scenario: Tablet portrait and landscape layouts
- **WHEN** the page is viewed on a tablet in portrait or landscape orientation
- **THEN** the layout adapts to the available space, keeps the timer readable, and displays all controls without horizontal overflow or clipping
