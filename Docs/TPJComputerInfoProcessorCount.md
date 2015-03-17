# ProcessorCount class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

```pascal
class function ProcessorCount: Integer;
```

## Description ##

Returns the number of processors installed in the computer. Mutli-core processors will report each core as a separate processor.