# Spec Delta

## ADDED Requirements

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
