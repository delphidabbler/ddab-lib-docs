# ReadWdwState method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

```pascal
procedure ReadWdwState(
  var Left, Top, Width, Height, State: Integer
); virtual; abstract;
```

## Description ##

Protected method used to read a window's size, position and state from storage.

This virtual abstract method must be overridden by descendant components to read the window's state, size and position information from a supported storage type.

The position of the window is returned in the _Left_ and _Top_ parameters, the size in the _Width_ and _Height_ parameters and the state in the _State_ parameter. _State_ should be the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`. The parameters are set to those currently existing for the associated window on calling the method.

_ReadWdwState_ is called internally by the _[Restore](TPJCustomWdwStateRestore.md)_ method.