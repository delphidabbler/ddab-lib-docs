# MajorVersion class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```pascal
class function MajorVersion: Integer;
```

## Description ##

Returns the major version number of the operating system.

The corresponding minor version number is provided by the _[MinorVersion](TPJOSInfoMinorVersion.md)_ method.

When the program is run in compatibility mode, this method will return the major version number of the "emulated" operating system.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will return the major version number of the installed operating system, regardless of any compatibility mode.