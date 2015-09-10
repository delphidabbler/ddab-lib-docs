# IsWindowsServer class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

**Introduced:** v5.0

```pascal
class function IsWindowsServer: Boolean;
```

## Description ##

Checks if the OS is a server version.

When running on Windows 2000 and later the result always relates to the actual OS, regardless of any compatibility mode in force. For versions prior to Windows 2000 this method will take note of compatibility modes and returns the same value as _[TPJOSInfo.IsServer](TPJOSInfoIsServer.md)_.
