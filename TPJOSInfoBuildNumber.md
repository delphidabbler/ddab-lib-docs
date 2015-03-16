<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# BuildNumber class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```
class function BuildNumber: Integer;
```

## Description ##

Returns the build number of the operating system.

When the program is run in compatibility mode, this method will return the build number of the "emulated" operating system.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will return the build number of the installed operating system, regardless of any compatibility mode.