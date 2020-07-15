# FileSubType property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property FileSubType: DWORD;
```

## Description

For some file types this run time property provides additional information about the type of file. The information is that specified in the fixed file information part of the _VERSIONINFO_ resource statement.

The value of this property is also provided by the the _dwFileSubType_ member of the _VS_FIXEDFILEINFO_ structure that is accessed using the [_FixedFileInfo_](./TPJVersionInfo-FixedFileInfo.md) property.

The value of _FileSubType_ depends on the file type identified by the [_FileType_](./TPJVersionInfo-FileType.md) property, as follows:

### Font files

When [_FileType_](./TPJVersionInfo-FileType.md) has value `VFT_FONT` (a font file) then valid values of _FileSubType_ are:

Flag                 | Description
---------------------|-------------
`VFT2_UNKNOWN`       | Font type is unknown.
`VFT2_FONT_RASTER`   | A raster font.
`VFT2_FONT_VECTOR`   | A vector font.
`VFT2_FONT_TRUETYPE` | A TrueType font.

### Device Drivers

When [_FileType_](./TPJVersionInfo-FileType.md) has value `VFT_DRV` (a device driver) then _FileSubType_ can take one of the following values:

Flag                   | Description
-----------------------|-------------
`VFT2_UNKNOWN`         | Driver type is unknown.
`VFT2_DRV_PRINTER`     | Printer driver.
`VFT2_DRV_KEYBOARD`    | Keyboard driver.
`VFT2_DRV_LANGUAGE`    | Language driver.
`VFT2_DRV_DISPLAY`     | Display driver.
`VFT2_DRV_MOUSE`       | Mouse driver.
`VFT2_DRV_NETWORK`     | Network driver.
`VFT2_DRV_SYSTEM`      | System driver.
`VFT2_DRV_INSTALLABLE` | Installable driver.
`VFT2_DRV_SOUND`       | Sound driver.
`VFT2_DRV_COMM`        | Communications driver.

### Virtual Device Drivers

When [_FileType_](./TPJVersionInfo-FileType.md) has value `VFT_VXD` (a virtual device driver) then _FileSubType_ contains the virtual device identifier included in the virtual device control block.

### Other Cases

In all other cases, including when there is no version information available, _FileSubType_ contains no information and should be zero.

Constants for all the values discussed above are defined in the _Windows_ unit.
