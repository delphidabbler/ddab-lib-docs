# [Version Information Component](../VerInfo.md) Overview

This project contains a component, [_TPJVersionInfo_](./API/TPJVersionInfo.md), which is a non-visual component that reads any version information contained in a 32 bit or 64 bit Windows executable file.

The component reads information from a designated file's [_VERSIONINFO_](http://msdn.microsoft.com/en-us/library/aa381058) resource. The required file is specified in the component's [_FileName_](./API/TPJVersionInfo-FileName.md) property. Setting [_FileName_](./API/TPJVersionInfo-FileName.md) to the empty string fetches version information for the executable file containing the component. The boolean [_HaveInfo_](./API/TPJVersionInfo-HaveInfo.md) property indicates whether the file contains version information. This component can access variable file information for each language provided in the resource.

Run-time properties enable access to to version information. Properties enable:

* Access to fixed file information, either by field or the whole record.
* Access to the number of translations stored in the version information.
* Selection of the translation for which information is to be returned by other properties.
* Access to the language and code page of the current translation, by code and by name.
* Access to the string file information for the current translation. Named properties access the Microsoft-defined string information, while an array property gives access to any string item by name.

Version numbers are encapsulated in [_TPJVersionNumber_](./API/TPJVersionNumber.md) records which, on Delphi 2006 or later, can be directly assigned to a string and can be compared using the normal equality operators. Helper functions are also provided for use with earlier Delphis that can format version numbers as text and can compare them.

The component makes calls to the Windows API when reading version information. Therefore the version information being read must follow the Microsoft guidelines. Be warned that not all software complies!

The project is compatible with all versions of the Delphi 32 bit and 64 bit native Windows compiler. It is not suitable for use with .NET.

For detailed information about version information refer to the Windows SDK.

## Links

* [Programmer's Guide](./API.md)
* [Examples](./Examples.md)
