<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# Description class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```
class function Description: string;
```

## Description ##

Returns a description of the operating system. The description depends on the available information and the platform.

For the Windows 9x platform systems the product name is given along with details of any service pack, e.g. Windows 98, Windows 98 SE.

For NT platform operating systems the name of the operating system is provided (e.g. Windows Vista or Windows NT) along with the edition (e.g. Professional), any service packs and the build number. On Windows NT the version number follows the product name.

When the program is run in compatibility mode, this method will return the description of the "emulated" operating system.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will return the description of the installed operating system, regardless of any compatibility mode.