# ProgramFilesX86 class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJSystemFolders](TPJSystemFolders.md)_

**Introduced:** v4.0

```pascal
class function ProgramFilesX86: string;
```

## Description ##

Returns the fully qualified path name of the system's Program Files x86 folder that is used for 32 bit programs running on 64 bit versions of Windows.

No such folder exists on 32 bit Windows and so _ProgramFilesX86_ returns the empty string on that platform.

**See also**

  * _[ProgramFiles](TPJSystemFoldersProgramFiles.md)_
  * _[ProgramFilesRedirect](TPJSystemFoldersProgramFilesRedirect.md)_