# FileName property

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

***Class:*** [_TPJVersionInfo_](./TPJVersionInfo.md)

```pascal
property FileName: string;
```

## Description

Specifies the file from which version information is to be read. A full path name should be provided.

Assigning a file name to this property at run time causes the given file to be checked for version information. The [_HaveInfo_](TPJVersionInfo-HaveInfo.md) property indicates whether any information was found in the file. When a value is assigned to _FileName_ at design time the component does not immediately check the file for version information -- this occurs when the component is created at run-time.

If _FileName_ is assigned the empty string (`''`) at run time the component reads version information from the host program file. The _FileName_ property is then set to program file's name. When `''` is assigned to _FileName_ at design time it retains this value until run-time when the program name is substituted. This arrangement works well when the component is hosted in an application. When the component is part of a DLL _FileName_ may not behave as expected.

The default value for _FileName_ is the empty string. This enables the component to automatically read version information from its program file without the user setting any properties or intervening if the program's executable file name is changed.
