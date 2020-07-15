# NumTranslations property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property NumTranslations: Integer;
```

## Description

Gets the number of translations in a file's version information.

Version information resources can contain variable information in more that one language / character set combination. [_TPJVersionInfo_](./TPJVersionInfo.md) defines each of these combinations as a "Translation". This property shows how many translations are available in a file's version information.

The property has value `0` if the file contains no translations or if the file has no version information.
