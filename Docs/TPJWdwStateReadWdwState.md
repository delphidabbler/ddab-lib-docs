# ReadWdwState method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

```pascal
procedure ReadWdwState(
  var Left, Top, Width, Height, State: Integer
); override;
```

## Description ##

_ReadWdwState_ is used  used to read a window's size, position and state from an ini file.

This protected method is overrridden by _[TPJWdwState](TPJWdwState.md)_ to read the window's state, size and position information from an ini file. Before reading the ini file _ReadWdwState_ triggers the _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ event (or, from v5.5, _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_) to enable the user to change the location and name of the ini file and the section within it from which to read the data.

The position of the window is returned in the _Left_ and _Top_ parameters, the size in the _Width_ and _Height_ parameters and the state in the _State_ parameter. _State_ is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`. The parameters are set to those currently existing for the associated window before calling the method.

This method is called by the _[Restore](TPJWdwStateRestore.md)_ method.