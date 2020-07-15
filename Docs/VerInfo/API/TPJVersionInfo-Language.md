# Language property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property Language: string;
```

## Description

Read only property that returns a string describing the language whose code is specified by the current translation. If the language code is unknown or there is no version information in the current file then the property returns the empty string.

To examine the actual language code instead of its descriptive name use the [_LanguageCode_](./TPJVersionInfo-LanguageCode.md) property instead.
