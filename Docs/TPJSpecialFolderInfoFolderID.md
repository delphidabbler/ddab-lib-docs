# FolderID property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJSpecialFolderInfo](TPJSpecialFolderInfo.md)_

```pascal
property FolderID: Integer;
```

## Description ##

Setting _FolderID_ to an appropriate `CSIDL_` value gets information about a special folder. When the property is set the information about the folder is stored in the component's run time read only properties.

The default value of _FolderID_ is `CSIDL_DESKTOP` - the desktop.

If _FolderID_ is set to an unknown value an exception will be raised. Use the _[IsValidSpecialFolderId](PJShellFoldersFunctions.md#isvalidspecialfolderid)_ function to check a folder ID for validity.
