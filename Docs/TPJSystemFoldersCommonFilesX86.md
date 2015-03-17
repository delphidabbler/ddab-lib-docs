# CommonFilesX86 class function #

**Project:** [System Information Unit](SystemInformationUnit.md).

**Unit:** _PJSysInfo_.

**Class:** _[TPJSystemFolders](TPJSystemFolders.md)_

**Introduced:** v4.0

```pascal
class function CommonFilesX86: string;
```

## Description ##

Returns the fully qualified path name of the system's Common Files x86 folder that is used for 32 bit programs running on 64 bit versions of Windows. This is usually a sub-folder of the Program Files x86 folder.

No such folder exists on 32 bit Windows and so _CommonFilesX86_ returns the empty string on that platform.

**See also**

  * _[CommonFiles](TPJSystemFoldersCommonFiles.md)_
  * _[CommonFilesRedirect](TPJSystemFoldersCommonFilesRedirect.md)_