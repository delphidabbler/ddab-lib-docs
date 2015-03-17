# DisplayName property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJSpecialFolderInfo](TPJSpecialFolderInfo.md)_

```pascal
property DisplayName: string;
```

## Description ##

This property gives the display name of the special folder specified by the _[FolderID](TPJSpecialFolderInfoFolderID.md)_ property. For physical folders (_[IsVirtual](TPJSpecialFolderInfoIsVirtual.md)_ is false), _DisplayName_ often (but not always) has the same value as the _[Path](TPJSpecialFolderInfoPath.md)_ property.

_DisplayName_ is set to the empty string if the special folder is not supported by the operating system (see _[IsSupported](TPJSpecialFolderInfoIsSupported.md)_).