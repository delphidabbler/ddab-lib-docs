# Save method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

```pascal
procedure Save;
```

## Description ##

This method saves the state, size and position of the owning form's window in an ini file.

If the ini file does not exist it is created. If it is not possible to create the file then the information is not saved.

For MDI child forms the window's top and left coordinates are relative to the MDI main form's client area. For other, top level, windows the coordinates are relative to the screen.

If the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is true then _Save_ is called automatically when the window is destroyed.

## Remarks ##

### v5.4.2 and earlier ###

The ini file name is determined by the _[IniFileName](TPJWdwStateIniFileName.md)_ property and the section within it used to store window state data is stored is determined by the _[Section](TPJWdwStateSection.md)_ property.

Any _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ event handler can override any of these property values.

If any of the directories in the path to the ini file name are not present then the save will fail and may raise an exception.

### v5.5.0 and later ###

The ini file name is determined by both the _[IniRootDir](TPJWdwStateIniRootDir.md)_ and _[IniFileName](TPJWdwStateIniFileName.md)_ properties and the section within the ini file used to store window state data is stored is determined by the _[Section](TPJWdwStateSection.md)_ property.

Any _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_ or _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ event handler can override any of these property values.

If any of the directories in the path to the ini file name are not present they will be created.