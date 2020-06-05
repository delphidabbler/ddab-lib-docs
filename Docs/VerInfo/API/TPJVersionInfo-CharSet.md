# CharSet property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property CharSet: string;
```

## Description

Read only property that returns a description of the character set whose code is specified by the current translation.

If the code is unknown or there is no version information in the current file then the empty string is returned.

To examine the actual character set code instead of its description use the [_CharSetCode_](./TPJVersionInfo-CharSetCode.md) property.
