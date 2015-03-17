# IsUACActive class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

**Introduced:** v4.0

```pascal
class function IsUACActive: Boolean;
```

## Description ##

Checks if UAC (user account control) is active on the host computer and returns True if so, or False if not.

Since UAC requires Windows Vista or later, False is always returned Windows XP and earlier.

**WARNING:** If the program is running on Windows Vista or later in Windows XP or earlier compatibility mode, _IsUACActive_ will always return False regardless of whether UAC is actually active or not.