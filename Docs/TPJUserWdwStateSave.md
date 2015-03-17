# Save method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJUserWdwState](TPJUserWdwState.md)_

```pascal
procedure Save;
```

## Description ##

This method saves the state, size and position of the owning form's window to persistent storage. The _[OnSaveData](TPJUserWdwStateOnSaveData.md)_ event is triggered by this method. The user must handle the event by saving the provided window state data.

For MDI child forms the window's top and left coordinates are relative to the MDI main form's client area. For other, top level, windows the coordinates are relative to the screen.

If the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is true then _Save_ is called automatically when the window is destroyed.