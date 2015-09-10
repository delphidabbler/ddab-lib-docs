# Processor class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

```pascal
class function Processor: TPJProcessorArchitecture;

type TPJProcessorArchitecture = (paUnknown, paX64, paIA64, paX86);
```

## Description ##

Returns a value from the _TPJProcessorArchitecture_ enumeration that describes the type of processor installed in the computer. Values of TPJProcessorArchitecture are:

| Value | Meaning |
|:------|:--------|
| `paUnknown` | Unknown processor. |
| `paX64` | X64 (AMD or Intel). |
| `paIA64` | Intel Itanium processor family. |
| `paX86` | Intel 32 bit x86. |
