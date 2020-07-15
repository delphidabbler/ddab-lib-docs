# FixedFileInfo property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property FixedFileInfo: TVSFixedFileInfo;
```

## Description

This read only property exposes the _TVSFixedFileInfo_ record for the current file. All members of the record are set to zeros if the current file contains no version information.

Note: the _TVSFixedFileInfo_ record is identical to the Windows _VS_FIXEDFILEINFO_ structure.

[_TPJVersionInfo_](./TPJVersionInfo.md) provides properties that can be used to directly access information contained in most of the fields of _TVSFixedFileInfo_. These are

* [_FileVersionNumber_](./TPJVersionInfo-FileVersionNumber.md)
* [_ProductVersionNumber_](./TPJVersionInfo-ProductVersionNumber.md)
* [_FileFlagsMask_](./TPJVersionInfo-FileFlagsMask.md)
* [_FileFlags_](./TPJVersionInfo-FileFlags.md)
* [_FileOS_](./TPJVersionInfo-FileOS.md)
* [_FileType_](./TPJVersionInfo-FileType.md)
* [_FileSubType_](./TPJVersionInfo-FileSubType.md)
