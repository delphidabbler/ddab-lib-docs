# HelpContext property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
type
  THelpContext = -MaxLongInt..MaxLongInt;

property HelpContext: THelpContext;
```

## Description ##

This property contains an integer value that determines which help topic appears when the user requests help. _HelpContext_ has effect only if the following conditions are met:

  * The _[HelpType](TPJBrowseDialogHelpType.md)_ property is set to `htContext`. (Delphi 6 and later only).
  * The dialog's help button is displayed, enabled and is clicked.
  * The F1 key if pressed and the _[Options](TPJBrowseDialogOptions.md)_ property does not include `boContextHelp`.

If _HelpContext_ is set to the default value of 0, and _[HelpType](TPJBrowseDialogHelpType.md)_ = `htContext` then any help button that is displayed is disabled.