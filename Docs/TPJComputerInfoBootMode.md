<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# BootMode class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJComputerInfo](TPJComputerInfo.md)_

**Introduced:** v3.1

```
class function BootMode: TPJBootMode;

type TPJBootMode = (bmUnknown, bmNormal, bmSafeMode, bmSafeModeNetwork);
```

## Description ##

Determines the operating system mode into which the the computer was booted.

Returns a value from the _TPJBootMode_ enumeration that describes the boot mode. Values of _TPJBootMode_ are:

| `bmUnknown` | Unknown boot mode. |
|:------------|:-------------------|
| `bmNormal` | Normal boot. |
| `bmSafeMode` | Booted in safe mode with no networking. |
| `bmSafeModeNetwork` | Booted in safe mode with networking. |