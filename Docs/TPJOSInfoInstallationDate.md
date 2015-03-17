# InstallationDate class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

**Introduced:** v5.0

```pascal
class function InstallationDate: TDateTime;
```

## Description ##

Returns the date the operating system was installed if known.

If the installation date is not known then `0.0` is returned. This is the date code for 30 December 1899.