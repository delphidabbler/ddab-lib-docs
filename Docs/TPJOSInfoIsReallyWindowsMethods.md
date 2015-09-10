# IsReallyWindowsXXX class methods #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

**Introduced:** v5.0

```pascal
class function IsReallyWindows2000OrGreater: Boolean;
class function IsReallyWindows2000SP1OrGreater: Boolean;
class function IsReallyWindows2000SP2OrGreater: Boolean;
class function IsReallyWindows2000SP3OrGreater: Boolean;
class function IsReallyWindows2000SP4OrGreater: Boolean;
class function IsReallyWindowsXPOrGreater: Boolean;
class function IsReallyWindowsXPSP1OrGreater: Boolean;
class function IsReallyWindowsXPSP2OrGreater: Boolean;
class function IsReallyWindowsXPSP3OrGreater: Boolean;
class function IsReallyWindowsVistaOrGreater: Boolean;
class function IsReallyWindowsVistaSP1OrGreater: Boolean;
class function IsReallyWindowsVistaSP2OrGreater: Boolean;
class function IsReallyWindows7OrGreater: Boolean;
class function IsReallyWindows7SP1OrGreater: Boolean;
class function IsReallyWindows8OrGreater: Boolean;
class function IsReallyWindows8Point1OrGreater: Boolean;
```

## Description ##

This set of methods check whether the operating system is that same as or greater (i.e. later) than a specified one, as follows:

| Method | Description |
|:-------|:------------|
| _IsReallyWindows2000OrGreater_ | Checks whether the OS is Windows 2000 or greater. |
| _IsReallyWindows2000SP1OrGreater_ | Checks whether the OS is Windows 2000 Service Pack 1 or greater. |
| _IsReallyWindows2000SP2OrGreater_ | Checks whether the OS is Windows 2000 Service Pack 2 or greater. |
| _IsReallyWindows2000SP3OrGreater_ | Checks whether the OS is Windows 2000 Service Pack 3 or greater. |
| _IsReallyWindows2000SP4OrGreater_ | Checks whether the OS is Windows 2000 Service Pack 4 or greater. |
| _IsReallyWindows7OrGreater_ | Checks whether the OS is Windows 7 or greater. |
| _IsReallyWindows7SP1OrGreater_ | Checks whether the OS is Windows 7 Service Pack 1 or greater. |
| _IsReallyWindows8OrGreater_ | Checks whether the OS is Windows 8 or greater. |
| _IsReallyWindows8Point1OrGreater_ | Checks whether the OS is Windows 8.1 or greater. |
| _IsReallyWindowsVistaOrGreater_ | Checks whether the OS is Windows Vista or greater. |
| _IsReallyWindowsVistaSP1OrGreater_ | Checks whether the OS is Windows Vista Service Pack 1 or greater. |
| _IsReallyWindowsVistaSP2OrGreater_ | Checks whether the OS is Windows Vista Service Pack 2 or greater. |
| _IsReallyWindowsXPOrGreater_ | Checks whether the OS is Windows XP or greater. |
| _IsReallyWindowsXPSP1OrGreater_ | Checks whether the OS is Windows XP Service Pack 1 or greater. |
| _IsReallyWindowsXPSP2OrGreater_ | Checks whether the OS is Windows XP Service Pack 2 or greater. |
| _IsReallyWindowsXPSP3OrGreater_ | Checks whether the OS is Windows XP Service Pack 3 or greater. |

Regardless of whether the program is running in compatibility these methods will always return information about the installed operating system.

These methods are identical in function to the functions with similar names that are declared in `versionhelpers.h`: see http://msdn.microsoft.com/en-us/library/windows/desktop/dn424972.aspx for details.
