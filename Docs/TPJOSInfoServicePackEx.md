# ServicePackEx class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

**Introduced:** v5.2

```pascal
class function ServicePackEx: string;
```

## Description

Returns a description of any installed operating service pack and/or other similar updates.

An empty string is returned if there is no service pack or update. 

If both a service pack and update are detected then the service pack description comes first, followed by a comma then the update description.

If a service pack is present it's description is identical to that returned from the _[ServicePack](TPJOSInfoServicePack.md)_ method.

On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will return the service pack or update details of the installed operating system, regardless of any compatibility mode.

## Remarks

Windows may add significant OS updates that bump the build number but do not declare themselves as service packs. 

> For example the Windows 10 TH2 update ("Version 1511") is to all intents and purposes a service pack. However it reports the same product version number and service pack version number as the 1st release of Windows 10. Only the build number is changed.

This method is used to report these updates in addition to service packs, while the _[ServicePack](TPJOSInfoServicePack.md)_ method only reports "official" service packs.
