# FileType property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property FileType: DWORD;
```

## Description

Use this read only run time property to get information about the type of file, e.g.application, DLL etc.

_FileType_ provides information about the type of file being examined. The information is as specified in the fixed file information part of the _VERSIONINFO_ resource statement.

The value of this property is also provided by the the dwFileType member of the _VS_FIXEDFILEINFO_ structure that is accessed using the [_FixedFileInfo_](./TPJVersionInfo-FixedFileInfo.md) property.

_FileType_ can take one of the values given in the following table. For some types of file further information is provided by the [_FileSubType_](./TPJVersionInfo-FileSubType.md) property.

Flag             | Description
-----------------|------------
`VFT_UNKNOWN`    | Unknown file type, or no version information is present.
`VFT_APP`        | Application.
`VFT_DLL`        | Dynamic-link library (DLL).
`VFT_DRV`        | Device driver. Further information is provided by the [_FileSubType_](./TPJVersionInfo-FileSubType.md)  property.
`VFT_FONT`       | Font file. Further information is provided by the [_FileSubType_](./TPJVersionInfo-FileSubType.md)  property.
`VFT_VXD`        | Virtual device driver. The [_FileSubType_](./TPJVersionInfo-FileSubType.md) property contains the virtual device identifier included in the virtual device control block.
`VFT_STATIC_LIB` | Static-link library.

The `VFT_XXX` constants are defined in the Windows unit.
