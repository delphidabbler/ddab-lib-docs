# HelpType property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
type
  THelpType = (htKeyword, htContext);

property HelpType: THelpType;
```

## Description ##

This property determines whether the _[HelpContext](TPJBrowseDialogHelpContext.md)_ or _[HelpKeyword](TPJBrowseDialogHelpKeyword.md)_ properties are used to identify the associated help topic.

When _HelpType_ = `htKeyword`, the _[HelpKeyword](TPJBrowseDialogHelpKeyword.md)_ property is used and _[HelpContext](TPJBrowseDialogHelpContext.md)_ is ignored. Conversely when _HelpType_ = `htContext`, _[HelpContext](TPJBrowseDialogHelpContext.md)_ is used and _[HelpKeyword](TPJBrowseDialogHelpKeyword.md)_ is ignored.

**Note:** This property is only available when the unit is compiled with Delphi 6 or later.