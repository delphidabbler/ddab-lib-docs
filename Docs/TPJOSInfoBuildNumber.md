# BuildNumber class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

```pascal
class function BuildNumber: Integer;
```

## Description ##

Returns the build number of the operating system.

When the program is run in compatibility mode, this method will return the build number of the "emulated" operating system.

[v5.0] On operating systems where _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False` this method will return the build number of the installed operating system, regardless of any compatibility mode.

### Notes

The method used to calculate the build number varies according to the version of the unit. This can result in slightly different results in cases where the build number can't be found.

* Before v5 the build number is obtained directly from the operating system.

* From v5.0.0 to v5.1.0 the build number is determined as before unless _[CanSpoof](TPJOSInfoCanSpoof.md)_ returns `False`. In this case the build number is calculated rather than being obtained directly from the operating system. If the build number can't be calculated then a value will be read from the registry.
  >**_BUG: Unfortunately it appears that the operating system can return the build number of an earlier operating system than that physically stored in the registry._**

* v5.2.0 and later use the same approach as for v5.0.0 except when the build number can't be calculated. In this case `0` is now returned to signal the error.

**See also**

  * _[RevisionNumber](TPJOSInfoRevisionNumber.md)_
