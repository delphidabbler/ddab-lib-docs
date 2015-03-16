<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# CanSpoof class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJOSInfo](TPJOSInfo.md)_

**Introduced:** v5.0

```
class function CanSpoof: Boolean;
```

## Description ##

Checks if the reported operating can be "spoofed" when the program is running in compatibility mode.

When this method returns `True` it indicates that some methods of _[TPJOSInfo](TPJOSInfo.md)_ and some global variables will return the details of the compatibility mode OS instead of the actual one.

When _CanSpoof_ returns `False` returned OS information will be the installed operating system and the operating system compatibility mode is ignored.

See the documentation of the relevant methods and global variables for details of which of them are affected by spoofing.