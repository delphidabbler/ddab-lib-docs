# FileFlagsMask property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property FileFlagsMask: DWORD;
```

## Description

_FileFlagsMask_ is a run time property containing a bitmask that determines which bits of the [_FileFlags_](./TPJVersionInfo-FileFlags.md) property are valid.

The property's value is specified in the fixed file information part of the _VERSIONINFO_ resource. See the [_FileFlags_](./TPJVersionInfo-FileFlags.md) topic for details of the available flags.

The value of this this property can also be obtained from the _dwFileFlagsMask_ field of the _VS_FIXEDFILEINFO_ structure, accessed using the [_FixedFileInfo_](./TPJVersionInfo-FixedFileInfo.md) property.
