# SaveWdwState method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJRegWdwState](TPJRegWdwState.md)_

```pascal
procedure SaveWdwState(
  const Left, Top, Width, Height, State: Integer
); override;
```

## Description ##

_SaveWdwState_ is used to write a window's size, position and state to the registry.

This protected method is overridden by _[TPJRegWdwState](TPJRegWdwState.md)_ to save the window's state, size and position information to the registry. Before saving the data _SaveWdwState_ triggers either the _[OnGetRegData](TPJRegWdwStateOnGetRegData.md)_ or the _[OnGetRegDataEx](TPJRegWdwStateOnGetRegDataEx.md)_**<sup>v5.6</sup>** event to enable the user to change the registry key to use to save the state data.

The position of the window is given by the _Left_ and _Top_ parameters, the size by the _Width_ and _Height_ parameters and the _State_ parameter is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`.

This method is called by the _[Save](TPJRegWdwStateSave.md)_ method.