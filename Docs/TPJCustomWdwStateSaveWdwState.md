# SaveWdwState method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

```pascal
procedure SaveWdwState(
  const Left, Top, Width, Height, State: Integer
); virtual; abstract;
```

## Description ##

Protected method used to write a window's size, position and state to storage.

This virtual abstract method must be overridden by descendant components to save the window's state, size and position to a supported storage type.

The position of the window is given by the _Left_ and _Top_ parameters, the size by the _Width_ and _Height_ parameters and the state by the _State_ parameter. _State_ is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`. The parameter values should be saved in a way that allows them to be identified and associated with the window when read back in.

_SaveWdwState_ is called internally by the _[Save](TPJCustomWdwStateSave.md)_ method.