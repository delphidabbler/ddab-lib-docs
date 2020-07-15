# StringFileInfo property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property StringFileInfo[const Name: string]: string;
```

## Description

Returns the value of the string file information with given name in the current translation.

This property can return both standard and custom string information. If the current file has no version information, or there is no string information for the current name, then the empty string is returned. Standard string information values are:

* Comments
* CompanyName
* FileDescription
* FileVersion
* InternalName
* LegalCopyright
* LegalTrademarks
* OriginalFileName
* PrivateBuild
* ProductName
* ProductVersion
* SpecialBuild

[_TPJVersionInfo_](./TPJVersionInfo.md) provides a dedicated string property with the same name as each of the above standard strings.

If your version information contains a custom string information entry named `'MyString'` in the current translation then you can extract its value with  code like:

```pascal
var
  X: string;
begin
  X := PJVersionInfo1.StringFileInfo['MyString'];
  // Do something with X
end;
```

Where _PJVersionInfo1_ is an instance of a [_TPJVersionInfo_](./TPJVersionInfo.md) component.
