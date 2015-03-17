# Headline property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
property Headline: string;
```

## Description ##

Stores text to be displayed in the _Browse for Folder_ dialog box.

The text is displayed above the tree view and is usually used to give instructions to the user or information about the purpose of the dialog box.

Changing the property when the dialog box is displayed (from one of the event handlers) does not change the text displayed in the dialog box.

The text displayed by _Headline_ should not be confused with the status text that can be displayed by handling the _[OnSelChange](TPJBrowseDialogOnSelChange.md)_ or _[OnSelChangeEx](TPJBrowseDialogOnSelChangeEx.md)_ events.