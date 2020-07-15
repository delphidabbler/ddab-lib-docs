# FileVersionNumber property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property FileVersionNumber: TPJVersionNumber;
```

## Description

This read only property gets the version number of the file being examined.

The version number is specified in the fixed file information part of the _VERSIONINFO_ resource statement.

The value of this property is derived from the _dwFileVersionMS_ and _dwFileVersionLS_ members of the *VS_FIXEDFILEINFO* structure that can be accessed using the [_FixedFileInfo_](./TPJVersionInfo-FixedFileInfo.md) property. The relationship between the fields of the [_TPJVersionNumber_](./TPJVersionNumber.md) record returned by this property and _dwFileVersionMS_ and _dwFileVersionLS_ is as follows:

_TPJVersionNumber_ field | _VS_FIXEDFILEINFO_ field
-------------------------|-------------------------
_V1_                     | `HiWord(dwFileVersionMS)`
_V2_                     | `LoWord(dwFileVersionMS)`
_V3_                     | `HiWord(dwFileVersionLS)`
_V4_                     | `LoWord(dwFileVersionLS)`

The value of _FileVersionNumber_ does not necessarily correspond to the string value given by the _FileVersion_† property as this is separately defined in the _VERSIONINFO_ resource statement.

## Footnote

† The _FileVersion_ property is an alias for the [_StringFileInfo[]_](./TPJVersionInfo-StringFileInfo.md) array property when 'FileVersion' is passed as the index
