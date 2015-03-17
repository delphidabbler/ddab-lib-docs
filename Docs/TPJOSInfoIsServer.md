# IsServer class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```pascal
class function IsServer: Boolean;
```

## Description ##

Returns true if the operating system is a server system or False if not.

When the program is run in compatibility mode, this method _may_ test whether the "emulated" operating system is a server. However, _this is not a reliable test_. For example when emulating a server operating system on a desktop system _IsServer_ continues to report `False`!.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will always check whether the installed operating system is a server, regardless of any compatibility mode.

[v5.0] When running on Windows 2000 and later you can use _[IsWindowsServer](TPJOSInfoIsWindowsServer.md)_ to ensure that compatibility mode has no effect on the returned value.