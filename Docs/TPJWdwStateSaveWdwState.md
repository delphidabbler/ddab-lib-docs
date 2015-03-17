# SaveWdwState method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

```pascal
procedure SaveWdwState(
  const Left, Top, Width, Height, State: Integer
); override;
```

## Description ##

_SaveWdwState_ is used to write a window's size, position and state to an ini file.

This protected method is overridden by _[TPJWdwState](TPJWdwState.md)_ to save the window's state, size and position information to an in file. Before saving the data _SaveWdwState_ triggers the _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ event (or, from v5.5, _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_) to enable the user to change the location and name of the ini file and the section within it where the data is to be saved.

The position of the window is given by the _Left_ and _Top_ parameters, the size by the _Width_ and _Height_ parameters and the _State_ parameter is the ordinal value of a member of the _TWindowState_ enumeration: `wsMinimized`, `wsMaximized` or `wsNormal`.

This method is called by the _[Save](TPJWdwStateSave.md)_ method.