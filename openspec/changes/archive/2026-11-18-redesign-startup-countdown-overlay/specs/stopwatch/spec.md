# Spec Delta

## ADDED Requirements

### Requirement: Present stopwatch startup countdown in a blinking overlay
During its fixed 10-second startup countdown, the stopwatch SHALL show a centered overlay above its interface with only the remaining whole-second number from 10 through 1. The number SHALL be large and bold, the surrounding interface SHALL be subdued, and the existing stop and reset controls SHALL remain usable.

#### Scenario: Show the stopwatch countdown overlay
- **WHEN** a new stopwatch startup countdown begins
- **THEN** a centered overlay displays only the remaining number from 10 through 1 in large, bold type over a subdued interface

#### Scenario: Blink between stopwatch countdown numbers
- **WHEN** the displayed whole-second value advances during the startup countdown
- **THEN** the current number briefly fades or disappears before the next number appears

#### Scenario: Cancel the stopwatch countdown from the overlay
- **WHEN** the user activates Stop or Reset while the overlay is shown
- **THEN** the countdown is cancelled according to the existing stopwatch timing behavior
