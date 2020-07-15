# FileOS property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property FileOS: DWORD;
```

## Description

_FileOS_ is a run time property that provides information about the operating system for which the application was designed.

The value is as specified in the fixed file information part of the _VERSIONINFO_ resource statement.

The same value can also be found by reading the _dwFileOS_ member of the _VS_FIXEDFILEINFO_ structure that is accessed using the [_FixedFileInfo_](./TPJVersionInfo-FixedFileInfo.md) property.

The value of _FileOS_ is made up of a combination of values. We first specify the host operating system, which can be one of:

Flag          | Description
--------------|------------
`VOS_NT`      | Windows NT
`VOS_DOS`     | MS-DOS
`VOS_OS232`   | 32 bit OS2
`VOS_OS216`   | 16 bit OS2
`VOS_UNKNOWN` | Any (or unspecified) host operating system

We then specify a target operating system that is running on one of the targets above by combining (ORing) one of the above with one of the following values:

Flag             | Description
-----------------|------------
`VOS__WINDOWS32` | 32 bit Windows
`VOS__WINDOWS16` | 16 bit Windows
`VOS__PM32`      | Presentation Manager 32
`VOS__PM16`      | Presentation Manager 16
`VOS__BASE`      | Any, unknown or unspecified target operating system

Some predefined combinations of the above flags are available. They are:

Flag                | Description
--------------------|------------
`VOS_DOS_WINDOWS16` | Windows 3.x running on MS-DOS
`VOS_DOS_WINDOWS32` | 32 bit Windows runing on MS-DOS
`VOS_OS216_PM16`    | Presentation Manager 16 running on 16 bit OS2
`VOS_OS232_PM32`    | Presentation Manager 32 running on 32 bit OS2
`VOS_NT_WINDOWS32`  | 32 bit Windows running on Windows NT

Symbolic constants for all the above flags are defined in the Windows unit.

Some of the flags are now obsolete - for example `VOS__PM32` and `_VOS_OS232` but may still exist in legacy programs.
