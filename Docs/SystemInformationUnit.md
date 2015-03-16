<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# System Information Unit #

This unit, _PJSysInfo_, contains a set of static classes that provide various pieces of system information. They are:

| **Class** | **Description** |
|:----------|:----------------|
| _[TPJComputerInfo](TPJComputerInfo.md)_ | Provides information about the computer system. |
| _[TPJSystemFolders](TPJSystemFolders.md)_ | Provides the paths of various standard system folders. |
| _[TPJOSInfo](TPJOSInfo.md)_ | Provides information about the operating system. |

The _PJSysInfo_ unit also defines a set of [global variables](PJSysInfoGlobals.md) that compliment and extend the operating system information provided by global variables defined in the _SysUtils_ unit.

Certain Windows types and constants not defined by Delphi that assist in working with extended operating system information are declared in this unit. Help on these definitions can be found on MSDN or in the Windows platform SDK.

## Changes in v5.0 ##

With the introduction of Windows 8.1 Microsoft has deprecated the _GetVersion_ and _GetVersionEx_ API functions that _PJSysInfo_ uses to get operating system version information. These API functions always return information about the reported operating system, which, when the program is running in compatibility mode, may be different to the true operating system. Furthermore _GetVersion_ will not detect Windows 8.1 correctly in all cases.

From version 5, to avoid using the deprecated API functions, a different approach is used to obtain version information when running on Windows 8.1 or later. This new method always returns information about the true operating system, regardless of any compatibility mode.

These changes mean that some of _[TPJOSInfo](TPJOSInfo.md)_'s methods and some [global variables](PJSysInfoGlobals.md) are affected by compatibility mode when run on operating systems prior to Windows 8.1, but will ignore compatibility mode on Windows 8.1 and later.  To help decide if compatibility mode will affect the returned information check the value returned from _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_ [v5.0]: `True` is returned if compatibility mode has an effect on the retrieved OS information and `False` is returned if not.

_It is unfortunate that the class's behaviour is no longer consistent across operating systems, but there is no choice if the code is to abide by Microsoft's much criticised decision to deprecate and possibly remove the old API._

v5.0 also adds some [new methods](TPJOSInfoIsReallyWindowsMethods.md) to _[TPJOSInfo](TPJOSInfo.md)_ that can be used to detect operating systems that always ignore compatibility mode.

## Deprecated & Removed Code ##

Versions of _PJSysInfo_ prior to v3.0 contained a set of deprecated routines and a deprecated component that duplicated a subset of the system information exposed by the classes and global variables above.

From v3.0 this deprecated code was not compiled unless the _PJSYSINFO\_COMPILE\_DEPRECATED_ symbol was defined before compiling the unit.

The deprecated code was removed entirely at v4.0.

## Conventions ##

This documentation relates to v3.x and v4.x of the System Information Unit.

Unless specified otherwise, classes, variables and methods are available in all versions from v3.0. Items that became available later are marked with the version at which they were introduced, for example [4.0].


---


**Links:**

  * Back to [Wiki Home Page](Welcome.md)
  * [System Information Unit Web Page](http://www.delphidabbler.com/software/sysinfo).