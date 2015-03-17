# MinorVersion class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```pascal
class function MinorVersion: Integer;
```

## Description ##

Returns the minor version number of the operating system.

The corresponding major version number is provided by the _[MajorVersion](TPJOSInfoMajorVersion.md)_ method.

When the program is run in compatibility mode, this method will return the minor version number of the "emulated" operating system.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will return the minor version number of the installed operating system, regardless of any compatibility mode.