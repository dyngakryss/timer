# Spec Delta

## REMOVED Requirements

### Requirement: Configure interval startup countdown
**Reason**: Startup countdown duration is fixed at 10 seconds for all timer modes and is no longer user-configurable.
**Migration**: No user action is required; new interval sessions use the fixed countdown.

### Requirement: Count down and advance through interval rounds
**Reason**: Its configurable startup-countdown behavior is replaced by a fixed 10-second startup countdown.
**Migration**: New sessions use the fixed countdown before round 1; round duration and round count remain configurable.

## ADDED Requirements

### Requirement: Run interval rounds with a fixed startup countdown
The interval timer SHALL count down each configured round and show round progress. A new session SHALL begin with a fixed 10-second countdown before round 1. Each next round SHALL begin immediately at full duration, and the final round SHALL stop at zero. Round status SHALL appear above the countdown at approximately 67% of its text size as “X of Y”, without a standalone large round numeral.

#### Scenario: Start an interval session
- **WHEN** the user starts a new interval session
- **THEN** the display shows the fixed 10-second startup countdown and “1 of <total>” above it at approximately 67% of the countdown text size

#### Scenario: Count down before the first round
- **WHEN** the 10-second startup countdown reaches zero
- **THEN** round 1 begins at its full configured duration

#### Scenario: Advance to the next round
- **WHEN** a round reaches zero and more configured rounds remain
- **THEN** the current round increases by one, the status above the countdown updates to “<current> of <total>”, and the next countdown begins immediately without a rest interval

#### Scenario: Complete the final round
- **WHEN** the final configured round reaches zero
- **THEN** the timer stops at zero and the status above the countdown shows “<total> of <total>” without additional text

#### Scenario: Keep round information accessible
- **WHEN** an interval round or its startup countdown is displayed
- **THEN** only the current and total values in “<current> of <total>” format appear above the countdown, the separate large round numeral is absent, and the status remains accessible to assistive technology

## MODIFIED Requirements

### Requirement: Pause, resume, and reset interval timing
The interval timer SHALL let the user cancel a startup countdown, pause a round without losing its remaining time or round progress, resume a paused round without repeating the startup countdown, and reset the session without changing its configured duration or round count.

#### Scenario: Stop during the startup countdown
- **WHEN** the user activates Stop during the interval startup countdown
- **THEN** the countdown is cancelled, the interval session remains unstarted at the configured round duration with round progress cleared, and Start is available to begin again

#### Scenario: Start again after cancelling the countdown
- **WHEN** the user starts an interval session after cancelling its startup countdown
- **THEN** a fresh 10-second startup countdown begins

#### Scenario: Pause and resume a round
- **WHEN** the user stops the interval timer during a round and later activates Start
- **THEN** the countdown resumes from the remaining time in that round without advancing the round during the pause or repeating the startup countdown

#### Scenario: Reset during the startup countdown
- **WHEN** the user activates Reset during the interval startup countdown
- **THEN** the countdown is cancelled, round progress clears, the display returns to the configured round duration, and the next start uses a fresh 10-second countdown

#### Scenario: Reset an interval session
- **WHEN** the user resets an interval session
- **THEN** timing stops, round progress clears, the display returns to the configured round duration, and the configured duration and round count remain available for the next session

## ADDED Requirements

### Requirement: Provide audible cues for interval startup
The interval timer SHALL play one short beep when each of 3, 2, and 1 seconds remains in the startup countdown, then play a 0.9-second beep that is slightly louder and lower-pitched when round 1 begins.

#### Scenario: Hear final countdown cues
- **WHEN** the startup countdown displays 3, 2, and 1 seconds remaining
- **THEN** one short beep plays at each displayed value

#### Scenario: Hear the interval start cue
- **WHEN** the startup countdown completes and round 1 begins
- **THEN** one 0.9-second beep plays at a slightly lower pitch and slightly louder than the short countdown beeps
