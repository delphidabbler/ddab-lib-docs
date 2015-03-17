# Restore method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

```pascal
procedure Restore;
```

## Description ##

This method restores the size and position of the owning form's window according to value saved in a specified section of an ini file. If the ini file or section do not exist then this method has no effect.

Various values of the _[Options](TPJCustomWdwStateOptions.md)_ property may cause either the saved size or state to be ignored or for the window to be repositioned (and possibly resized) to fit within the desktop's work area.

If the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is true _Restore_ is called automatically when the window is created.

## Remarks ##

### v5.4.2 and earlier ###

The ini file name is determined by the _[IniFileName](TPJWdwStateIniFileName.md)_ property and the section within it that contains the window state data is determined by the _[Section](TPJWdwStateSection.md)_ property.

Any _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ event handler can override any of these property values.

### v5.5.0 and later ###

The ini file name is determined by both the _[IniRootDir](TPJWdwStateIniRootDir.md)_ and _[IniFileName](TPJWdwStateIniFileName.md)_ properties and the section within it that contains the window state data is determined by the _[Section](TPJWdwStateSection.md)_ property.

Any _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_ or _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ event handler can override any of these property values.