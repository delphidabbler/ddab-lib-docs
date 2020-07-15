# ProductVersionNumber property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property ProductVersionNumber: TPJVersionNumber;
```

## Description

This read only property gets the version number of the product to which the file being examined relates.

The version number is specified in the fixed file information part of the _VERSIONINFO_ resource statement.

The value of this property is derived from the _dwProductVersionMS_ and _dwProductVersionLS_ members of the *VS_FIXEDFILEINFO* structure that can be accessed using the [_FixedFileInfo_](./TPJVersionInfo-FixedFileInfo.md) property. The relationship between the fields of the [_TPJVersionNumber_](./TPJVersionNumber.md) record returned by this property and _dwProductVersionMS_ and _dwProductVersionLS_ is as follows:

_TPJVersionNumber field_ | _VS_FIXEDFILEINFO_ field
-------------------------|-------------------------
_V1_                     | `HiWord(dwProductVersionMS)`
_V2_                     | `LoWord(dwProductVersionMS)`
_V3_                     | `HiWord(dwProductVersionLS)`
_V4_                     | `LoWord(dwProductVersionLS)`

The value of _ProductVersionNumber_ does not necessarily correspond to the string value given by the _ProductVersion_† property as this is separately defined in the _VERSIONINFO_ resource statement.

## Footnote

† The _ProductVersion_ property is an alias for the [_StringFileInfo[]_](./TPJVersionInfo-StringFileInfo.md) array property when 'ProductVersion' is passed as the index.
