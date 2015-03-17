# IsAdmin class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

**Introduced:** v4.0

```pascal
class function IsAdmin: Boolean;
```

## Description ##

Checks if the current user has administrator privileges and returns True if so, or False if not.

True is always returned on the Windows 95 platform, since there is no real concept of "administrator" on the platform.

**WARNING:** If the program is running on a Windows NT platform operating system in Windows 9x compatibility mode, _IsAdmin_ will always return True regardless of whether the user actually has admin privileges or not.