# Spec Delta

## MODIFIED Requirements

### Requirement: Navigate timer modes with visible tabs, horizontal swipes, and keyboard arrows
The timer page SHALL let users move among Stopwatch, Intervals, and Tabata in that order using visible tabs, horizontal swipes, or left and right arrow keys. The tabs SHALL use the tablist pattern, expose the selected mode with `aria-selected`, and let arrow keys focus and select only an adjacent tab without wrapping. Arrow keys on the focused timer interface and horizontal swipes SHALL remain navigation shortcuts. The selected timer mode SHALL be identifiable to assistive technology without visible carousel instructions or timer-position text.

#### Scenario: Select a mode by clicking or tapping a tab
- **WHEN** the user clicks or taps an enabled tab for another timer mode
- **THEN** that mode is selected and presented, and its tab exposes the selected state

#### Scenario: Navigate timer modes with tab arrow keys
- **WHEN** a tab has focus and the user presses the left or right arrow key while navigation is allowed and an adjacent mode exists
- **THEN** focus and selection move to the adjacent tab, and the newly selected mode is presented

#### Scenario: Navigate timer modes with keyboard shortcuts
- **WHEN** the timer interface has focus and the user presses the left or right arrow key while navigation is allowed and an adjacent mode exists
- **THEN** the adjacent timer mode in the order Stopwatch, Intervals, Tabata is selected and presented

#### Scenario: Swipe to another timer mode
- **WHEN** the user swipes left or right while timer-mode navigation is allowed and an adjacent mode exists in that direction
- **THEN** the adjacent timer mode in the order Stopwatch, Intervals, Tabata is selected and presented

#### Scenario: Stay at navigation endpoints
- **WHEN** the user navigates left from Stopwatch or right from Tabata using a tab arrow key, interface shortcut, or swipe
- **THEN** the selected timer mode remains unchanged

#### Scenario: Expose the selected mode to assistive technology
- **WHEN** any timer mode is displayed
- **THEN** its tab exposes `aria-selected="true"`, the other tabs expose `aria-selected="false"`, and no visible carousel instruction or timer-position text is shown

### Requirement: Prevent mode changes while a timer is active
The timer page SHALL prevent timer-mode changes while the selected timer is running or in a countdown, including a Tabata startup countdown, work period, or rest period, without interrupting the active timer. The tabs SHALL be disabled while mode changes are prevented.

#### Scenario: Attempt to switch while running
- **WHEN** the user tries to select another tab, swipes, or presses a navigation arrow while a timer is running
- **THEN** the tabs are disabled, the selected mode does not change, and the timer continues running

#### Scenario: Attempt to switch during countdown
- **WHEN** the user tries to select another tab, swipes, or presses a navigation arrow while a timer countdown is active
- **THEN** the tabs are disabled, the selected mode does not change, and the countdown continues

#### Scenario: Attempt to switch during Tabata work or rest
- **WHEN** the user tries to select another tab, swipes, or presses a navigation arrow during a Tabata work or rest period
- **THEN** the tabs are disabled, the selected mode does not change, and the active period continues

#### Scenario: Switch after stopping
- **WHEN** the user stops the selected timer and then selects or navigates to another mode
- **THEN** the tabs are enabled and the other timer mode is selected without starting or resetting it

### Requirement: Present timer mode titles in a consistent heading position
The timer page SHALL keep an accessible heading for the active mode section without displaying a duplicate visible mode label beside the Settings control. The selected tab SHALL provide the visible mode name, and the accessible heading SHALL match it.

#### Scenario: Identify the active mode without a duplicate visible heading
- **WHEN** any timer mode is displayed
- **THEN** its selected tab visibly identifies the mode, its accessible heading matches the mode, and no duplicate visible mode label appears beside the Settings control

#### Scenario: Change the active mode heading
- **WHEN** the user switches between modes with and without a Settings control
- **THEN** the accessible heading and selected tab update to the new mode, and the Settings control retains its existing visibility behavior

## ADDED Requirements

### Requirement: Preserve the main landmark and structure timer content
The timer page SHALL expose exactly one main landmark using native main semantics, group the active timer interface in a section named for the selected mode, and not expose the page as a carousel.

#### Scenario: Identify the main landmark
- **WHEN** assistive technology reads the page landmarks
- **THEN** it lists exactly one main landmark and the timer page is not identified as a carousel

#### Scenario: Identify the active timer section
- **WHEN** a timer mode is displayed
- **THEN** its timer interface is grouped in a section whose accessible name matches the selected mode

### Requirement: Update the document title for the selected timer mode
The page's document title SHALL match the name of the selected timer mode.

#### Scenario: Set the initial document title
- **WHEN** the timer page first loads
- **THEN** its document title is “Stopwatch”

#### Scenario: Update the document title after switching modes
- **WHEN** the user selects Intervals or Tabata
- **THEN** the document title updates to the selected mode's name
