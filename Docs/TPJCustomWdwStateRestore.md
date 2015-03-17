# Restore method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJCustomWdwState](TPJCustomWdwState.md)_

```pascal
procedure Restore;
```

## Description ##

This method restores the size, position and state of the owning form's window according to saved values.

Various values of the _[Options](TPJCustomWdwStateOptions.md)_ property may cause either the saved size or state to be ignored or for the window to be repositioned (and possibly resized) to fit within the appropriate monitor's desktop work area.

If the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is true _Restore_ is called automatically when the window is created. If _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ is false then _Restore_ must be called from code to restore the window. The form's _OnShow_ event handler is a good place to do this.