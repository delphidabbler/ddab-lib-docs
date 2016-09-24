# OnGetIniDataEx event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

**Introduced:** v5.5

```pascal
type
  TPJWdwStateGetIniDataEx = procedure(
    var AIniRootDir: TPJWdwStateIniRootDir;
    var AIniFilename, ASection: string
  ) of object;

property OnGetIniDataEx: TPJWdwStateGetIniDataEx;
```

## Description ##

_OnGetIniDataEx_ allows user to change the directory and name of the ini file and the section within it where window information is stored.

The event is triggered in the following cicumstances:

  * Just before the ini file is read when restoring a window
  * Just before the ini file is written when saving window information.
  * When the _[IniFilePath](TPJWdwStateIniFilePath.md)_ method is called.

The directory location, name of the ini file and the section within it are passed as var parameters to the event handler, allowing the user to change the values, and hence the location where the window data is recorded. The values passed to the event handler are the same as those of the _[IniRootDir](TPJWdwStateIniRootDir.md)_, _[IniFileName](TPJWdwStateIniFileName.md)_ and _[Section](TPJWdwStateSection.md)_ properties.

Changing the values of the event's parameters _does not_ change the value of the related properties.

The purpose of the event is to enable the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property to be used without setting the _[IniRootDir](TPJWdwStateIniRootDir.md)_, _[IniFileName](TPJWdwStateIniFileName.md)_ and _[Section](TPJWdwStateSection.md)_ properties at design time - i.e. handling the event allows any of these property values to be overridden.

Changing the values of the _AIniRootDir_, _AIniFileName_ or _ASection_ parameters has exactly the same effect on the ini file and section names as setting the _[IniRootDir](TPJWdwStateIniRootDir.md)_, _[IniFileName](TPJWdwStateIniFileName.md)_ or _[Section](TPJWdwStateSection.md)_ properties to the same values. See the documentation of those properties for details.

If the path to the resulting ini file does not exist it is created, if possible, when the component first attempts to write data to the file. If the required directories can't be created an exception will be raised.

**Note:** _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ is not fired if a handler is assigned to the _OnGetIniDataEx_ event - you should only provide an event handler one event or the other, not both.
