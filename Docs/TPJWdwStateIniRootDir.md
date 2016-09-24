# IniRootDir property #

**Project:** [Window State Components](WindowStateComponents.md).

**Unit:** _PJWdwState_.

**Class:** _[TPJWdwState](TPJWdwState.md)_

**Introduced:** v5.5

```pascal
type
  TPJWdwStateIniRootDir = (
    rdWindowsDir, rdExeDir, rdAppDataDir, rdProgramDataDir
  );

property IniRootDir: TPJWdwStateIniRootDir;
```

## Description ##

This property determines the root directory to be used for any relative ini file name specified by the _[IniFileName](TPJWdwStateIniFileName.md)_ property.

Possible values are:

| Value | Notes |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rdAppDataDir` | Places the ini file in a _sub-directory_ of the per user application directory, i.e. `%appdata%`. If the file name given by _[IniFileName](TPJWdwStateIniFileName.md)_ does not specify the required sub-directory then the file is stored in the `%appdata%\DelphiDabbler\WindowStateStore` directory. |
| `rdProgramDataDir` | Places the ini file in a _sub-directory_ of the common application data directory, i.e. `%programdata%`. If the file name given by _[IniFileName](TPJWdwStateIniFileName.md)_ does not specify the required sub-directory then the file is stored in the `%programdata%\DelphiDabbler\WindowStateStore` directory. |
| `rdExeDir` | Places the ini file in the same directory as the program's executable file. This option should not be used for programs stored in the _Program Files_ directory - see below. |
| `rdWindowsDir` | Places the ini file in the Windows system directory, i.e. `%systemroot%`. This option should only be used for backwards compatibility with earlier versions of the component - see below. |


In cases where _[IniFileName](TPJWdwStateIniFileName.md)_ is an absolute path _IniRootDir_ is ignored.

The full file path of the ini file can be found by calling the _[IniFilePath](TPJWdwStateIniFilePath.md)_ method.

## Remarks ##

The value of _IniRootDir_ can be overridden at run time if you handle either the _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_ event. This can be useful when the _[AutoSaveRestore](TPJCustomWdwStateAutoSaveRestore.md)_ property is `True` and you want to specify the root directory at run time. In this case setting _IniRootDir_ at run time will not work because the form will be restored before you have an opportunity to change the property value. However the _[OnGetIniDataEx](TPJWdwStateOnGetIniDataEx.md)_ event is triggered before the form restores, enabling the root directory to be specified.

You are strongly recommended **not** to use the `rdWindowsDir` value for _IniRootDir_ to store the ini file in the Windows directory. On Windows Vista and later an attempt to write to the Windows directory may be redirected to the virtual store. `rdWindowsDir` is provided only for backward compatibility will earlier versions of _[TPJWdwState](TPJWdwState.md)_. See the to get the _[IniFileName](TPJWdwStateIniFileName.md)_ property documentation for more information.

You should set _IniRootDir_ to `rdExeDir` if the executable program if it is stored in the _Program Files_ directory (or similar), since you may not have write access to it or the file may be redirected to a virtual store. `rdExeDir` is provided mainly for use with portable programs that save confguration data either with, or in sub-directories or, their installation directory.
