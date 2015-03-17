# Create method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

```pascal
constructor Create(AOwner: TComponent);
```

## Description ##

This class constructor permits only one instance of a component derived from _TPJCustomWdwState_ to be placed on a form at any one time. This restriction is enforced since it makes no sense to have more that one component saving and restoring the window's size, position and state.

**Note:** This constructor cannot be used to create components dynamically at run-time and therefore must never be called directly from source code. Use the _[CreateStandAlone](TPJCustomWdwStateCreateStandAlone.md)_ constructor instead.