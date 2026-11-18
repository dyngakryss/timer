# timer-mode-navigation Specification

## Purpose

Lets users move between available timer types in the timer page using a horizontal carousel while preserving access to each timer mode.

## Requirements

### Requirement: Navigate timer modes with horizontal swipes and keyboard arrows
The timer page SHALL let users move among Stopwatch, Intervals, and Tabata in that order by swiping horizontally or by using the left and right arrow keys when the timer-mode carousel has keyboard focus. Navigation SHALL select only an adjacent mode and SHALL not wrap at either end. The currently selected timer mode SHALL be identifiable to assistive technology, without visible carousel instructions or timer-position text.

#### Scenario: Swipe to another timer mode
- **WHEN** the user swipes left or right while timer-mode navigation is allowed and an adjacent mode exists in that direction
- **THEN** the adjacent timer mode in the order Stopwatch, Intervals, Tabata is selected and presented

#### Scenario: Navigate timer modes by keyboard
- **WHEN** the timer-mode carousel has keyboard focus and the user presses the left or right arrow key while navigation is allowed and an adjacent mode exists in that direction
- **THEN** the adjacent timer mode in the order Stopwatch, Intervals, Tabata is selected and presented

#### Scenario: Stay at carousel endpoints
- **WHEN** the user navigates left from Stopwatch or right from Tabata
- **THEN** the selected timer mode remains unchanged

#### Scenario: Show mode without carousel guidance or position text
- **WHEN** any timer mode is displayed
- **THEN** no visible carousel instruction or timer-position text is shown, and the selected timer mode remains identifiable to assistive technology

### Requirement: Prevent mode changes while a timer is active
The timer page SHALL prevent timer-mode changes while the selected timer is running or in a countdown, including a Tabata startup countdown, work period, or rest period, without interrupting the active timer.

#### Scenario: Attempt to switch while running
- **WHEN** the user swipes or presses a navigation arrow while a timer is running
- **THEN** the selected mode does not change and the timer continues running

#### Scenario: Attempt to switch during countdown
- **WHEN** the user swipes or presses a navigation arrow while a timer countdown is active
- **THEN** the selected mode does not change and the countdown continues

#### Scenario: Attempt to switch during Tabata work or rest
- **WHEN** the user swipes or presses a navigation arrow while a Tabata work or rest period is active
- **THEN** the selected mode does not change and the active period continues

#### Scenario: Switch after stopping
- **WHEN** the user stops the selected timer and then navigates to another mode
- **THEN** the other timer mode is selected without starting or resetting it
