# LanguageCode property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property LanguageCode: WORD;
```

## Description

_LanguageCode_ is a read only property that returns the language code associated with the current translation.

If the current file has no version information then `0` is returned. To get a description of the language use the [_Language_](./TPJVersionInfo-Language.md) property instead.

See the 'langID' section of the [MSDN VERSIONINFO](http://msdn.microsoft.com/en-us/library/aa381058) topic for information about these codes.
