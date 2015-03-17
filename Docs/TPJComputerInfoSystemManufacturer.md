# SystemManufacturer class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

**Introduced:** v4.0

```pascal
class function SystemManufacturer: string;
```

## Description ##

Returns the name of the host computer's manufacturer.

The returned name does not include the computer's model (product) name. To get that, use the _[SystemProductName](TPJComputerInfoSystemProductName.md)_ property.