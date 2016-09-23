# Description class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```pascal
class function Description: string;
```

## Description ##

Returns a description of the operating system. The description depends on the available information and the platform.

For the Windows 9x platform systems the product name is given along with details of any service pack, e.g. Windows 98, Windows 98 SE.

For NT platform operating systems the name of the operating system is provided (e.g. Windows Vista or Windows NT) along with the edition (e.g. Professional), any service packs and the build number. On Windows NT the version number follows the product name.

When the program is run in compatibility mode, this method will return the description of the "emulated" operating system.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will return the description of the installed operating system, regardless of any compatibility mode.

_Description_ includes information about any service packs from the _[ServicePack](TPJOSInfoServicePack.md)_ property.

[v5.3] _Description_ now gets service pack information from the _[ServicePackEx](TPJOSInfoServicePackEx.md)_ property instead of _[ServicePack](TPJOSInfoServicePack.md)_. This ensures that _Description_ contains information about updates that aren't classed as service packs, for e.g. Windows 10 Version 1607.
