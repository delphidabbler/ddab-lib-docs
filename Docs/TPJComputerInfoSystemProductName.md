# SystemProductName class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

**Introduced:** v4.0

```pascal
class function SystemProductName: string;
```

## Description ##

Returns the model (product) name of the host computer.

The returned name does not include the computer's manufacturer. To get that, use the _[SystemManufacturer](TPJComputerInfoSystemManufacturer.md)_ property.