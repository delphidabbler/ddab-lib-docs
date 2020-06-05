# TPJVersionInfo class

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

## Description

This class defines a non-visual component that exposes version resource information contained in an executable file.

The component reads information from the file's [_VERSIONINFO_](http://msdn.microsoft.com/en-us/library/aa381058) resource. If the file has no such resource then the component returns no information. Use the [_HaveInfo_](./TPJVersionInfo-HaveInfo.md) property to find whether the component has been able to get version information from the file.

The file from which resource information is gleaned is determined by the [_FileName_](./TPJVersionInfo-FileName.md) property. This is the only design-time property added by this component. Other properties are available at run time only and are used to manipulate and read the version information.

The component supports multi-lingual version resources which have different sets of string information for each language. Use the [_NumTranslations_](./TPJVersionInfo-NumTranslations.md) and [_CurrentTranslation_](./TPJVersionInfo-CurrentTranslation.md) properties to select the required translation.

### Methods

_TPJVersionInfo_ defines no methods.

### Properties

_TPJVersionInfo_ defines the following properties in addition to those inherited from _TComponent_.

Property | Description
---------|------------
[_CharSet_](./TPJVersionInfo-CharSet.md) | Returns a description of the character set for the current translation.
[_CharSetCode_](TPJVersionInfo-CharSetCode.md) | Returns the code of the character set used by the current translation.
_Comments_ | Returns the 'Comments' string file information string. This property is an alias for [_StringFileInfo[`'Comments'`]_](TPJVersionInfo-StringFileInfo.md).
_CompanyName_ | Returns the 'CompanyName' string file information string. This property is an alias for [_StringFileInfo[`'CompanyName'`]_](./TPJVersionInfo-StringFileInfo.md).
[_CurrentTranslation_](./TPJVersionInfo-CurrentTranslation.md) | Get or set the translation to be used by string information, language and character set properties.
_FileDescription_ | Returns the 'FileDescription' string file information string. This property is an alias for [_StringFileInfo[`'FileDescription'`]_](./TPJVersionInfo-StringFileInfo.md).
[_FileFlags_](./TPJVersionInfo-FileFlags.md) | Provides information about the release attributes of a file.
[_FileFlagsMask_](./TPJVersionInfo-FileFlagsMask.md) | Determines which bits of the [_FileFlags_](./TPJVersionInfo-FileFlags.md) property are valid.
[_FileName_](./TPJVersionInfo-FileName.md) | Specifies the file from which version information is to be read.
[_FileOS_](./TPJVersionInfo-FileOS.md) | Provides information about the operating system for which the application was designed.
[_FileSubType_](./TPJVersionInfo-FileSubType.md) | Provides additional file type information for certain file types.
[_FileType_](./TPJVersionInfo-FileType.md) | Provides information about the type of file: e.g. application, DLL etc.
_FileVersion_ | Returns the 'FileVersion' string file information string. This property is an alias for [_StringFileInfo[`'FileVersion'`]_](./TPJVersionInfo-StringFileInfo.md).
[_FileVersionNumber_](./TPJVersionInfo-FileVersionNumber.md) | Gets the version number of a file as a [_TPJVersionNumber_](./TPJVersionNumber.md) record.
[_FixedFileInfo_](./TPJVersionInfo-FixedFileInfo.md) | Provides access to the fixed file information record from the current file via a Windows _TVSFixedFileInfo_ record.
[_HaveInfo_](./TPJVersionInfo-HaveInfo.md) | Informs if the current file contains version information.
_InternalName_ | Returns the 'InternalName' string file information string. This property is an alias for [_StringFileInfo[`'InternalName'`]_](./TPJVersionInfo-StringFileInfo.md).
[_Language_](./TPJVersionInfo-Language.md) | Returns a description of the language used for the current translation.
[_LanguageCode_](./TPJVersionInfo-LanguageCode.md) | Returns the language code associated with the current translation.
_LegalCopyright_ | Returns the 'LegalCopyright' string file information string. This property is an alias for [_StringFileInfo[`'LegalCopyright'`]_](./TPJVersionInfo-StringFileInfo.md).
_LegalTrademarks_ | Returns the 'LegalTrademarks' string file information string. This property is an alias for [_StringFileInfo[`'LegalTrademarks'`]_](./TPJVersionInfo-StringFileInfo.md).
[_NumTranslations_](./TPJVersionInfo-NumTranslations.md) | Gets the number of translations in a file's version information.
_OriginalFileName_ | Returns the 'OriginalFileName' string file information string. This property is an alias for [_StringFileInfo[`'OriginalFileName'`]_](./TPJVersionInfo-StringFileInfo.md).
_PrivateBuild_ | Returns the 'PrivateBuild' string file information string. This property is an alias for [_StringFileInfo[`'PrivateBuild'`]_](./TPJVersionInfo-StringFileInfo.md).
_ProductName_ | Returns the 'ProductName' string file information string. This property is an alias for [_StringFileInfo[`'ProductName'`]_](./TPJVersionInfo-StringFileInfo.md).
_ProductVersion_ | Returns the 'ProductVersion' string file information string. This property is an alias for [_StringFileInfo[`'ProductVersion'`]_](./TPJVersionInfo-StringFileInfo.md).
[_ProductVersionNumber_](./TPJVersionInfo-ProductVersionNumber.md) | Gets the version number of the product to which a file relates as a [TPJVersionNumber](./TPJVersionNumber.md) record.
_SpecialBuild_ | Returns the 'SpecialBuild' string file information string. This property is an alias for [_StringFileInfo[`'SpecialBuild'`]_](./TPJVersionInfo-StringFileInfo.md).
[_StringFileInfo_](./TPJVersionInfo-StringFileInfo.md) | String indexed array property that returns the value of string information with the given name.

### Events

_TPJVersionInfo_ defines no new events.
