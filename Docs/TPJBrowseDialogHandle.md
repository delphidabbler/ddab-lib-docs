# Handle property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
property Handle: THandle;
```

## Description ##

This property provides access to the _Browse for Folder_ dialog box's window handle while the _[Execute](TPJBrowseDialogExecute.md)_ method is active. At other times _Handle_ is set to 0. _Handle_ therefore only references a valid window handle when the dialog box is displayed.

_Handle_ is intended for use in the _[OnInitialise](TPJBrowseDialogOnInitialise.md)_, _[OnSelChange](TPJBrowseDialogOnSelChange.md)_, _[OnSelChangeEx](TPJBrowseDialogOnSelChangeEx.md)_, _[OnValidationFailed](TPJBrowseDialogOnValidationFailed.md)_ and _[OnClose](TPJBrowseDialogOnClose.md)_ events whenever it is necessary to customise the window's behaviour.