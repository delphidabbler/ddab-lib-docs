# IsVirtual property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJSpecialFolderInfo](TPJSpecialFolderInfo.md)_

```pascal
property IsVirtual: Boolean;
```

## Description ##

Use _IsVirtual_ to determine if the current special folder is virtual or not.

When the property is false the special folder specified by _[FolderID](TPJSpecialFolderInfoFolderID.md)_ the folder is a physical folder in the file system and the _[Path](TPJSpecialFolderInfoPath.md)_ property gives its location. When _IsVirtual_ is true then the folder is not physically present in the file system and the _[Path](TPJSpecialFolderInfoPath.md)_ property is set to the empty string.

_IsVirtual_ is set to false if the special folder is not supported by the operating system (see _[IsSupported](TPJSpecialFolderInfoIsSupported.md)_).