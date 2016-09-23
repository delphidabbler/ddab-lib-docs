# RootFolderID property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
property RootFolderID: Integer;
```

## Description ##

_RootFolderID_ specifies the identifier of the special folder that is used as the root of the folder tree displayed in the dialog box. The property defaults to `CSIDL_DESKTOP`.

All valid values that can be stored in _RootFolderID_ can be found using the _[TPJSpecialFolderEnum](TPJSpecialFolderEnum.md)_ enumerator class. An identifier can be tested for validity using the _[IsValidSpecialFolderId](PJShellFoldersFunctions.md#isvalidspecialfolderid)_ function.

Assigning an invalid value to the property causes an exception to be raised. Not all special folder identifiers are supported on all versions of Windows. Attempting to display a folder that is not supported by the operating system will cause an exception to be raised. Use the _[TPJSpecialFolderInfo](TPJSpecialFolderInfo.md)_ component to test if a special folder is supported without raising an exception.
