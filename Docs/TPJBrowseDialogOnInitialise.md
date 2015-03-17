# OnInitialise event #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
property OnInitialise: TNotifyEvent;
```

## Description ##

_OnInitialise_ occurs when the dialog initialises.

This event is triggered after the dialog has opened and the default folder has been selected but before the dialog is displayed. Because of this the _[OnSelChange](TPJBrowseDialogOnSelChange.md)_ and _[OnSelChangeEx](TPJBrowseDialogOnSelChangeEx.md)_ events will usually fire before _OnInitialise_. The dialog's window handle is available via the _[Handle](TPJBrowseDialogHandle.md)_ property.

Write an _OnInitialise_ event handler to perform special processing when the dialog is intialised.