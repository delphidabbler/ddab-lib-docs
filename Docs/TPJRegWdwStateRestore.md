# Restore method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJRegWdwState](TPJRegWdwState.md)_

```pascal
procedure Restore;
```

## Description ##

This method restores the size and position of the owning form's window according to value saved in a specified part of the Windows registry. The root and sub keys of the registry where the information is stored are specfied by the _[RootKey](TPJRegWdwStateRootKey.md)_ or _[RootKeyEx](TPJRegWdwStateRootKeyEx.md)_**<sup>v5.6</sup>**  and _[SubKey](TPJRegWdwStateSubKey.md)_ properties. If the key does not exist in the registry then this method has no effect.

Various values of the _[Options](TPJCustomWdwStateOptions.md)_ property may cause either the saved size or state to be ignored or for the window to be repositioned (and possibly resized) to fit within the desktop's work area.

If the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is true _Restore_ is called automatically when the window is created.