# Restore method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJUserWdwState](TPJUserWdwState.md)_

```pascal
procedure Restore;
```

## Description ##

This method restores the size and position of the owning form's window according to value saved in persistent storage. The _[OnReadData](TPJUserWdwStateOnReadData.md)_ event is triggered by this method. The user must handle the event by reading and passing back the required window state data.

Various values of the _[Options](TPJCustomWdwStateOptions.md)_ property may cause either the saved size or state to be ignored or for the window to be repositioned (and possibly resized) to fit within the desktop's work area.

If the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is true _Restore_ is called automatically when the window is created.