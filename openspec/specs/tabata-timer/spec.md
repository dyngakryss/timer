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

### Requirement: Run Tabata work and rest rounds
The Tabata timer SHALL count down each round's work duration followed by its rest duration, including after the final work period, and complete after the final rest. It SHALL show round progress during the session. A new session SHALL begin with a fixed 10-second startup countdown before the first work period.

#### Scenario: Begin the first work period
- **WHEN** the user starts a new Tabata session
- **THEN** the fixed 10-second startup countdown is shown before the first work period begins

#### Scenario: Begin the first work period after startup
- **WHEN** the 10-second startup countdown reaches zero
- **THEN** the first work period begins at its full configured duration

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
The Tabata timer SHALL let the user cancel a startup countdown, pause a work or rest period without losing its remaining time or round progress, resume without repeating the startup countdown, and reset without changing the configured work duration, rest duration, or round count.

#### Scenario: Stop during startup countdown
- **WHEN** the user activates Stop during the Tabata startup countdown
- **THEN** the countdown is cancelled, the session returns to its unstarted state, and Start is available

#### Scenario: Start again after cancelling the countdown
- **WHEN** the user starts a Tabata session after cancelling its startup countdown
- **THEN** a fresh 10-second startup countdown begins

#### Scenario: Pause and resume a work or rest period
- **WHEN** the user stops the timer during a work or rest period and later starts it again
- **THEN** the same phase resumes from its remaining time without changing round progress or repeating the startup countdown

#### Scenario: Reset a Tabata session
- **WHEN** the user activates Reset during a startup countdown, work period, rest period, paused session, or completed session
- **THEN** timing stops, progress clears, the display returns to the configured initial state, and the configured work duration, rest duration, and round count remain available for the next session

### Requirement: Present Tabata startup countdown in a blinking overlay
During its fixed 10-second startup countdown, the Tabata timer SHALL show a centered overlay above its interface with only the remaining whole-second number from 10 through 1. The number SHALL be large and bold, the surrounding interface SHALL be subdued, and existing timer controls and round status SHALL remain available.

#### Scenario: Show the Tabata countdown overlay
- **WHEN** a new Tabata startup countdown begins
- **THEN** a centered overlay displays only the remaining number from 10 through 1 in large, bold type over a subdued interface

#### Scenario: Blink between Tabata countdown numbers
- **WHEN** the displayed whole-second value advances during the startup countdown
- **THEN** the current number briefly fades or disappears before the next number appears

#### Scenario: Cancel the Tabata countdown from the overlay
- **WHEN** the user activates Stop or Reset while the overlay is shown
- **THEN** the countdown is cancelled according to the existing Tabata timer behavior and the round-status information remains outside the overlay

### Requirement: Provide audible cues for Tabata startup
The Tabata timer SHALL play one short beep when each of 3, 2, and 1 seconds remains in the startup countdown, then play a 0.9-second beep that is slightly louder and lower-pitched when the first work period begins.

#### Scenario: Hear final countdown cues
- **WHEN** the startup countdown displays 3, 2, and 1 seconds remaining
- **THEN** one short beep plays at each displayed value

#### Scenario: Hear the Tabata start cue
- **WHEN** the startup countdown completes and the first work period begins
- **THEN** one 0.9-second beep plays at a slightly lower pitch and slightly louder than the short countdown beeps
