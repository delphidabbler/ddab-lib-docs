# IsWinNT class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```pascal
class function IsWinNT: Boolean;
```

## Description ##

Returns True if an NT operating system is installed (including Windows 2000, Windows XP, Windows Vista, Windows 7, Windows 8, Windows 8.1, Windows 2003 Server, Windows 2008 Server, Windows 2008 Server R 2, Windows 2012 Server and Windows 2012 Server R 2), or False otherwise.

When the program is run in compatibility mode, this method will report whether the "emulated" operating system is a Windows NT operating system.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will always return `True`, because _[CanSpoof](TPJOSInfoCanSpoof.md)_ only ever returns `False` on NT systems.