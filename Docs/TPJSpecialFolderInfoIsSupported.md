# IsSupported property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJSpecialFolderInfo](TPJSpecialFolderInfo.md)_

```pascal
property IsSupported: Boolean;
```

## Description ##

Use _IsSupported_ to determine if the current special folder is supported by the operating system.

This property returns true if the special folder specified by _[FolderID](TPJSpecialFolderInfoFolderID.md)_ is supported on the operating system and false if it is not. When _IsSupported_ is false the component's other properties have zero values: _[IsVirtual](TPJSpecialFolderInfoIsVirtual.md)_ is false and _[DisplayName](TPJSpecialFolderInfoDisplayName.md)_ and _[Path](TPJSpecialFolderInfoPath.md)_ are empty strings.