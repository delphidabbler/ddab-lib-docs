# TPJOSInfo #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

This is a static class that gives access to information about the operating system on which the program is running. All the class' functionality is exposed through its static methods. Because it is static the class does not need to be instantiated before use.

When the host program is run in compatibility mode many of _TPJOSInfo_'s methods will be spoofed into returning information about the emulated operating system.

[v5.0] Compatibility mode has no effect on information returned by any of _TPJOSInfo_'s methods when running on Windows 8.1 or later. Use the _[TPJOSInfo.CanSpoof](TPJOSInfoCanSpoof.md)_ [v5.0] method to find out if the returned information _could_ have been spoofed.

[v5.0 ] _TPJOSInfo_ also provides some [new methods](TPJOSInfoIsReallyWindowsMethods.md) that can be used to query the operating system version regardless of any compatibility mode.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[BuildNumber](TPJOSInfoBuildNumber.md)_ | Gets the operating system build number. |
| _[CanSpoof](TPJOSInfoCanSpoof.md)_ [v5.0] | Checks if the OS can be "spoofed" by specifying a compatibility mode for the program. |
| _[Description](TPJOSInfoDescription.md)_ | Gets a full information about of an operating system version. |
| _[Edition](TPJOSInfoEdition.md)_ | Gets the edition of an operating system product. |
| _[HasPenExtensions](TPJOSInfoHasPenExtensions.md)_ | Checks for Windows Pen Extensions. |
| _[InstallationDate](TPJOSInfoInstallationDate.md)_ [v5.0] | Gets the date that Windows was installed. |
| _[IsMediaCenter](TPJOSInfoIsMediaCenter.md)_ | Checks for Windows Media Center. |
| _[IsReallyWindows2000OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows 2000 or greater. Ignores compatibility mode. |
| _[IsReallyWindows2000SP1OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows 2000 Service Pack 1 or greater. Ignores compatibility mode. |
| _[IsReallyWindows2000SP2OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows 2000 Service Pack 2 or greater. Ignores compatibility mode. |
| _[IsReallyWindows2000SP3OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows 2000 Service Pack 3 or greater. Ignores compatibility mode. |
| _[IsReallyWindows2000SP4OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows 2000 Service Pack 4 or greater. Ignores compatibility mode. |
| _[IsReallyWindows7OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0]| Checks whether the OS is Windows 7 or greater. Ignores compatibility mode. |
| _[IsReallyWindows7SP1OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows 7 Service Pack 1 or greater. Ignores compatibility mode. |
| _[IsReallyWindows8OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows 8 or greater. Ignores compatibility mode. |
| _[IsReallyWindows8Point1OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows 8.1 or greater. Ignores compatibility mode. |
| _[IsReallyWindowsVistaOrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows Vista or greater. Ignores compatibility mode. |
| _[IsReallyWindowsVistaSP1OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows Vista Service Pack 1 or greater. Ignores compatibility mode. |
| _[IsReallyWindowsVistaSP2OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows Vista Service Pack 2 or greater. Ignores compatibility mode. |
| _[IsReallyWindowsXPOrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows XP or greater. Ignores compatibility mode. |
| _[IsReallyWindowsXPSP1OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows XP Service Pack 1 or greater. Ignores compatibility mode. |
| _[IsReallyWindowsXPSP2OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows XP Service Pack 2 or greater. Ignores compatibility mode. |
| _[IsReallyWindowsXPSP3OrGreater](TPJOSInfoIsReallyWindowsMethods.md)_ [v5.0] | Checks whether the OS is Windows XP Service Pack 3 or greater. Ignores compatibility mode. |
| _[IsRemoteSession](TPJOSInfoIsRemoteSession.md)_ [v3.3] | Checks for a Windows Terminal Server remote session. |
| _[IsServer](TPJOSInfoIsServer.md)_ | Checks for a server operating system. |
| _[IsTabletPC](TPJOSInfoIsTabletPC.md)_ | Checks for Windows Tablet PC. |
| _[IsWin32s](TPJOSInfoIsWin32s.md)_ | Checks for the Windows 32s system. |
| _[IsWin9x](TPJOSInfoIsWin9x.md)_ | Checks for the Windows 95 platform. |
| _[IsWindowsServer](TPJOSInfoIsWindowsServer.md)_ [v5.0] | Checks if the OS is a server version. (When run in compatibility mode on Windows 2000 and later this method returns the true OS, unlike _[IsServer](TPJOSInfoIsServer.md)_). |
| _[IsWinNT](TPJOSInfoIsWinNT.md)_ | Checks for the Windows NT platform. |
| _[IsWow64](TPJOSInfoIsWow64.md)_ | Checks if the program is running on WOW64. |
| _[MajorVersion](TPJOSInfoMajorVersion.md)_ | Gets the operating system major version. |
| _[MinorVersion](TPJOSInfoMinorVersion.md)_ | Gets the operating system minor version. |
| _[Platform](TPJOSInfoPlatform.md)_ | Gets the operating system platform. |
| _[Product](TPJOSInfoProduct.md)_ | Gets a code representing the operating system product. |
| _[ProductID](TPJOSInfoProductID.md)_ | Gets the Windows product ID. |
| _[ProductName](TPJOSInfoProductName.md)_ | Gets the name of the operating system product. |
| _[RegisteredOrganisation](TPJOSInfoRegisteredOrganisation.md)_ [v4.0] | Gets the name of the organisation to which Windows is registered. |
| _[RegisteredOwner](TPJOSInfoRegisteredOwner.md)_ [v4.0] | Gets the name of the person owning this copy of Windows. |
| _[RevisionNumber](TPJOSInfoRevisionNumber.md)_ [5.6] | Gets the operating system's revision number, if any. |
| _[ServicePack](TPJOSInfoServicePack.md)_ | Gets details of the operating system's service pack. |
| _[ServicePackEx](TPJOSInfoServicePackEx.md)_ [v5.2] | Gets details of the operating system's service pack or any other significant update. |
| _[ServicePackMajor](TPJOSInfoServicePackMajor.md)_ | Gets the operating system's major service pack version number. |
| _[ServicePackMinor](TPJOSInfoServicePackMinor.md)_ | Gets the operating system's minor service pack version number. |

## Properties ##

_TPJOSInfo_ defines no properties.

## Events ##

_TPJOSInfo_ defines no events.