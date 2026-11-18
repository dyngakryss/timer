# Spec Delta

## MODIFIED Requirements

### Requirement: Control stopwatch timing
The stopwatch SHALL allow the user to start or resume timing, stop timing without clearing elapsed time, and reset elapsed time to zero. Starting a new timing attempt from zero SHALL begin a fixed 10-second countdown; starting after pausing SHALL resume immediately without another countdown.

#### Scenario: Start timing
- **WHEN** the user activates Start while the stopwatch is at zero and stopped
- **THEN** the stopwatch displays a 10-second startup countdown before elapsed timing begins

#### Scenario: Stop and resume timing
- **WHEN** the user activates Stop while the stopwatch is running and later activates Start
- **THEN** the stopwatch pauses at its elapsed time and resumes from that time without counting the paused interval or repeating the startup countdown

#### Scenario: Cancel the startup countdown
- **WHEN** the user activates Stop or Reset during the startup countdown
- **THEN** the countdown is cancelled, the stopwatch remains stopped at 00:00, and a later Start begins a new 10-second countdown

#### Scenario: Reset timing
- **WHEN** the user activates Reset
- **THEN** the stopwatch stops and displays 00:00

### Requirement: Show countdown before stopwatch timing
Starting the stopwatch from zero SHALL display a 10-second countdown in minutes and seconds, then automatically begin stopwatch timing at 00:00 when the countdown reaches zero.

#### Scenario: Countdown reaches zero
- **WHEN** the 10-second countdown reaches zero
- **THEN** stopwatch timing begins from 00:00

#### Scenario: Cancel countdown with Stop
- **WHEN** the user activates Stop during the startup countdown
- **THEN** the countdown is cancelled, the stopwatch remains stopped at 00:00, and Start is available to begin a fresh 10-second countdown

#### Scenario: Cancel countdown with Reset
- **WHEN** the user activates Reset during the startup countdown
- **THEN** the countdown is cancelled, the stopwatch remains stopped at 00:00, and the next start uses a fresh 10-second countdown

## ADDED Requirements

### Requirement: Provide audible cues for stopwatch startup
The stopwatch SHALL play one short beep when each of 3, 2, and 1 seconds remains in its startup countdown, then play a 0.9-second beep that is slightly louder and lower-pitched when stopwatch timing begins.

#### Scenario: Hear final countdown cues
- **WHEN** the startup countdown displays 3, 2, and 1 seconds remaining
- **THEN** one short beep plays at each displayed value

#### Scenario: Hear the stopwatch start cue
- **WHEN** the startup countdown completes and stopwatch timing begins
- **THEN** one 0.9-second beep plays at a slightly lower pitch and slightly louder than the short countdown beeps

## REMOVED Requirements

### Requirement: Configure startup countdown from Settings
**Reason**: Startup countdown duration is fixed at 10 seconds for all timer modes and is no longer user-configurable.
**Migration**: No user action is required; new stopwatch starts use the fixed countdown. Remove the stopwatch-only Settings control because it has no remaining settings.

