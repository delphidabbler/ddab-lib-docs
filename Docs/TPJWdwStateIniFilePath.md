# IniFilePath method #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

**Introduced:** v5.5

```pascal
function IniFilePath: string
```

## Description ##

This method returns the fully specified file name of the ini file used to store window state information.

The return value depends on the the values of the _[IniRootDir](TPJWdwStateIniRootDir.md)_ and _[IniFileName](TPJWdwStateIniFileName.md)_ properties as modified by the values returned from any _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_ or _[OnGetIniData](TPJWdwStateOnGetIniData.md)_ event handlers.