# SaveWdwState method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJUserWdwState](TPJUserWdwState.md)_

```pascal
procedure SaveWdwState(
  const Left, Top, Width, Height, State: Integer
); override;
```

## Description ##

_SaveWdwState_ is used to write a window's size, position and state to persitent storage.

This protected method is overrridden by _[TPJUserWdwState](TPJUserWdwState.md)_ to trigger the _[OnSaveData](TPJUserWdwStateOnSaveData.md)_ event that the user must handle to save the window's state, size and position information.

The position of the window is given by the _Left_ and _Top_ parameters, the size by the _Width_ and _Height_ parameters and the _State_ parameter is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`.

This method is called by the _[Save](TPJUserWdwStateSave.md)_ method.