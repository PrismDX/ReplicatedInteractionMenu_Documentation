# ReplicatedInteractionMenu Changelog

### v1.2 - *01. Sept 2025*
* Added Hold to interact.

### v1.15 - *30. Nov 2024*

#### Animations:
* Added Fade in / fade out animation to interaction menu.
* Added fade pulse effect to interaction element when interacting.
* added 2 new variables to control animation speed ( InputFeedbackSpeed & MenuFadeSpeed in InteractionManager component ).

#### Visual:
* Added lables to actions which allows us to change display text for each action.
* Fixed issue with menu positioning when menu element got too big.
* Changed variable "Mode" to "Replication" for easier understanding.

#### Conditions
- Added Condition system which allows us to remove menu options if conditions are not met.
- Added a variable ( bRequireAllConditions ).
- Added the option to require all conditions or just one to display menu element.
- Added conditions array to InteractionManager component for comparison.
- Added condition structure.
- Added condition enumerator.
- Added a variable ( bUseInterfaceCondition ) used for more complex conditions for displaying menu elements.

#### Additional:
- Added RIMInteractionInterface for dynamic labels and custom conditions.
---