# DisplayName property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
property DisplayName: string;
```

## Description ##

This property provides the display name of the folder the user selected or entered in the dialog box. This name is the same as that displayed in the dialog box. If the selected folder is a physical folder in the file system then _DisplayName_ contains the name of the folder whose full path is specified in the _[FolderName](TPJBrowseDialogFolderName.md)_ property. If the user cancelled the dialog box then _DisplayName_ is not updated.

If _DisplayName_ is set to the empty string then no folder has yet been selected by the user.

The property is run time and read only.

**See also:**
  * _[FolderName](TPJBrowseDialogFolderName.md)_