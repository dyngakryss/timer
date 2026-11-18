# tabata-timer Specification

## Purpose

Provides a configurable work-and-rest timer for Tabata-style training, including a finite round count and an optional preparation countdown.

## Requirements

### Requirement: Configure Tabata work, rest, and rounds
The Tabata timer SHALL let the user configure positive work and rest durations in minutes:seconds format and a positive whole-number round count from Tabata Settings. Initial values SHALL be 00:20 work, 00:10 rest, and 8 rounds; applied values SHALL remain in effect for the current page session.

#### Scenario: Apply Tabata settings
- **WHEN** the user applies valid work duration, rest duration, and round count values
- **THEN** the values are used for the next Tabata session

#### Scenario: Reject invalid Tabata settings
- **WHEN** the user applies a malformed or non-positive work or rest duration, or a non-positive or fractional round count
- **THEN** the invalid settings are not accepted and the user can correct them

### Requirement: Configure Tabata startup countdown
The Tabata timer SHALL let the user configure a non-negative whole number of startup countdown seconds in Tabata Settings. The initial setting SHALL be zero, and an applied value SHALL remain in effect for the current page session and be used for the next new Tabata session.

#### Scenario: Apply Tabata startup countdown
- **WHEN** the user applies a valid whole number of startup countdown seconds
- **THEN** that value is used before the next new Tabata session starts

#### Scenario: Reject invalid Tabata startup countdown
- **WHEN** the user attempts to apply an empty, negative, fractional, or otherwise invalid startup countdown
- **THEN** the value is not accepted and the user can correct it

#### Scenario: Start immediately with zero startup countdown
- **WHEN** the user has not configured a startup countdown or its value is zero
- **THEN** a new Tabata session begins its first work period immediately

### Requirement: Run Tabata work and rest rounds
The Tabata timer SHALL count down each round's work duration followed by its rest duration, including after the final work period, and complete after the final rest. It SHALL show round progress during the session.

#### Scenario: Begin the first work period
- **WHEN** a new Tabata session starts with a positive startup countdown
- **THEN** the startup countdown is shown before the first work period begins at its full configured duration

#### Scenario: Transition from work to rest
- **WHEN** a work period reaches zero
- **THEN** the timer immediately begins that round's rest period at its full configured duration and identifies the phase as Rest

#### Scenario: Advance after a rest period
- **WHEN** a rest period reaches zero and more rounds remain
- **THEN** the round number increases and the next work period begins immediately at its full configured duration

#### Scenario: Rest after the final work period
- **WHEN** the final work period reaches zero
- **THEN** the final round's rest period begins immediately at its full configured duration

#### Scenario: Complete after the final rest period
- **WHEN** the final round's rest period reaches zero
- **THEN** the session completes at zero and the final round progress remains shown

#### Scenario: Identify round progress
- **WHEN** a Tabata work period, rest period, or startup countdown is displayed
- **THEN** only the current and total round values appear as “X of Y” above the countdown, without visible phase text, and the round status remains accessible to assistive technology

### Requirement: Pause, resume, stop, and reset Tabata
The Tabata timer SHALL let the user cancel a startup countdown, pause a work or rest period without losing its remaining time or round progress, resume without repeating the startup countdown, and reset without changing configured settings.

#### Scenario: Stop during startup countdown
- **WHEN** the user activates Stop during the Tabata startup countdown
- **THEN** the countdown is cancelled, the session returns to its unstarted state, and Start is available

#### Scenario: Pause and resume a work or rest period
- **WHEN** the user stops the timer during a work or rest period and later starts it again
- **THEN** the same phase resumes from its remaining time without changing round progress or repeating the startup countdown

#### Scenario: Reset a Tabata session
- **WHEN** the user activates Reset during a startup countdown, work period, rest period, paused session, or completed session
- **THEN** timing stops, progress clears, the display returns to the configured initial state, and all configured settings remain available for the next session
