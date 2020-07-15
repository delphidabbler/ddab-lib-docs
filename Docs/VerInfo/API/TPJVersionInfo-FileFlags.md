# FileFlags property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property FileFlags: DWORD;
```

## Description

Use this read-only property to get information about the release attributes of a file.

_FileFlags_ holds information (as a bit-set) about the attributes of the file as specified in the fixed file information part of a _VERSIONINFO_ resource.

File flags information is also provided by the _dwFileFlags_ member of the _VS_FIXEDFILEINFO_ structure which can be accessed using the [_FixedFileInfo_](./TPJVersionInfo-FixedFileInfo.md) property.

The bit set can contain any of the following values:

Flag | Description
-----|--------
`VS_FF_DEBUG` | File contains debugging information.
`VS_FF_INFOINFERRED` | Some of the members in this structure may be empty or incorrect.
`VS_FF_PATCHED` | The file is not identical to the original file with the same version number.
`VS_FF_PRERELEASE` | The file is a development version.
`VS_FF_PRIVATEBUILD` | The file is not a standard release. If this flag is set then the PrivateBuild_† property may yield further information.
`VS_FF_SPECIALBUILD` | The file is a variation of a standard release with the same version number. If this flag is set then the _SpecialBuild_† property may yeild further information.

The `VS_FF_XXX` constants are defined in the _Windows_ unit.

The [_FileFlagsMask_](./TPJVersionInfo-FileFlagsMask.md) property determines which of the bits in this flag are valid.

## Footnote

† The _PrivateBuild_ and _SpecialBuild_ properties are aliases of the [_StringFileInfo[]_](./TPJVersionInfo-StringFileInfo.md) property when passed `'PrivateBuild'` and `'SpecialBuild'` respectively as index parameters.
