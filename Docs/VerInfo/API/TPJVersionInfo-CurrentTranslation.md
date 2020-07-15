# CurrentTranslation property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property CurrentTranslation: Integer;
```

## Description

This run time property gets or sets the translation to be used by the string file information, language and character set related properties.

Version information resources can contain variable information in more that one langauge / character set combination. [_TPJVersionInfo_](./TPJVersionInfo.md) defines each of these combinations as a "Translation".

Translations are specified by assigning a zero based index to the _CurrentTranslation_ property. Valid values are in the range `0` to one less than the total number of translations. The number of translations can be found be reading the [_NumTranslations_](./TPJVersionInfo-NumTranslations.md) property. If an attempt is made to set _CurrentTranslation_ outside this range then the property is given the value `-1`.

_CurrentTranslation_ is set to `0` when a file is first accessed (i.e. when the [_FileName_](./TPJVersionInfo-FileName.md) property is assigned or when the component is first created) or `-1` if there is no version information in a file.
