# OnGetIniData event #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

```pascal
type
  TPJWdwStateGetIniData = procedure(
    var AIniFilename, ASection: string
  ) of object;

property OnGetIniData: TPJWdwStateGetIniData;
```

## Description ##

_OnGetIniData_ allows the user to change the name of the ini file and the section within it where window information is stored.

The event is triggered in the following circumstances:

  * Just before the ini file is read when restoring a window.
  * Just before the ini file is written when saving window information.
  * <sup>v5.5</sup> When the _[IniFilePath](TPJWdwStateIniFilePath.md)_ method is called.

The name of the ini file and the section within it are passed as var parameters to the event handler, allowing the user to change the values, and hence the location where the window data is recorded.  The values passed to the event handler are the same as those of the _[IniFileName](TPJWdwStateIniFileName.md)_ and _[Section](TPJWdwStateSection.md)_ properties.

Changing the values of the event's parameters _does not_ change the value of the related properties.

The purpose of the event is to enable the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property to be used without setting the _[IniFileName](TPJWdwStateIniFileName.md)_ and _[Section](TPJWdwStateSection.md)_ properties at design time - i.e. handling the event allows either or both of the default _[IniFileName](TPJWdwStateIniFileName.md)_ and _[Section](TPJWdwStateSection.md)_ names to be overridden.

_[TPJWdwState](TPJWdwState.md)_'s behaviour when the event handler returns depends on the values of the parameters it returns. This behaviour changed at v5.5, as described below.

### v5.4.2 and earlier ###

If you change the _AIniFileName_ parameter it has the following effect on the file name used for the ini file. You should note that this effect differs slightly from if you had set the related properties.

| **Value of _AIniFileName_** | **Effect on ini file name** |
|:----------------------------|:----------------------------|
| Empty string | **Error**. The file name will be the empty string and is likely to lead to an exception. |
| Relative file name | The ini file name is as specified by _AIniFileName_ and it is stored in the Windows installation directory. For example if _AIniFileName_ is `Foo.ini` the result is an ini file name of `C:\Windows\Foo.ini` or simlar while a value of `Foo\Bar.ini` would save window state data in `C:\Windows\Foo\Bar.ini`. |
| Absolute file name | The ini file is stored in the given path, which much exist, or an exception is raised. |

Changing the _ASection_ parameter changes the name of the section used to store the window state information in the ini file. **Do not** set _Section_ to the empty string because this may have unexpected results.

### v5.5.0 and later ###

Changing the values of the _AIniFileName_ or _ASection_ parameters has exactly the same effect on the ini file and section names as setting the _[IniFileName](TPJWdwStateIniFileName.md)_ or _[Section](TPJWdwStateSection.md)_ properties to the same values. The full name of the ini file is also influenced by the value of the _[IniRootDir](TPJWdwStateIniRootDir.md)_ property. See the documentation of those properties for details.

If the path to the ini file does not exist it is created, if possible, when the component first attempts to write data to the file. If the required directories can't be created an exception will be raised.

**Note:** _OnGetIniData_ is not fired if a handler is assigned to the _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_ event - you should only provide an event handler one event or the other, not both.
