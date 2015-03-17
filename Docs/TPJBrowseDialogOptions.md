# Options property #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
type
  TPJBrowseDlgOption = (
    boShowHelp, boContextHelp, boStatusText, boDirsOnly, boNewDlgStyle,
    boHideMakeFolderBtn, boEditBox, boHint
  );
type TPJBrowseDlgOptions = set of TPJBrowseDlgOption;

property Options: TPJBrowseDlgOptions;
```

## Description ##

Use the _Options_ property to customize the appearance and functionality of the dialog. One or more of the following values can be assigned to the property:

| **Value** | **Meaning** |
|:----------|:------------|
| `boShowHelp` | Displays a help button in the dialog box. When the user clicks the button the application's help file is activated at the topic given by the component's _[HelpContext](TPJBrowseDialogHelpContext.md)_ or _[HelpKeyword](TPJBrowseDialogHelpKeyword.md)_ properties. When _[HelpContext](TPJBrowseDialogHelpContext.md)_ is 0 or _[HelpKeyword](TPJBrowseDialogHelpKeyword.md)_ is the empty string the button is disabled. If _Options_ does not include `boContextHelp` then pressing F1 has the same effect as clicking the _Help_ button. **Note:** This option is ignored when `boNewStyleDlg` is included in _Options_. |
| `boContextHelp` | Displays a **?** button in the dialog's title bar. Clicking the **?** button and then clicking a control in the dialog brings up context sensitive popup help on each control in a window. Pressing F1 has the same effect. In this case the help relates to the currently active control. **Note:** this option only works on some operating systems. It does not work on Windows Vista, for example. |
| `boStatusText` | Permits status information to be displayed in the dialog box in response to selection changes. To cause this text to appear either the _[OnSelChange](TPJBrowseDialogOnSelChange.md)_ or the _[OnSelChangeEx](TPJBrowseDialogOnSelChangeEx.md)_ event must be handled and the required text sent back to the dialog box via the event handler's _StatusText_ parameter. **Note:** This option is ignored when `boNewStyleDlg` is included in _Options_. |
| `boDirsOnly` | Causes the dialog box to display only folders in the file system. The _OK_ button is disabled by default if the selected folder is virtual. If this option is omitted then file system and virtual folders are provided and any folder can be selected. **Note:** If `boNewDlgStyle` is specified executing the dialog box with a virtual folder selected as the root folder can cause an error message to be displayed. |
| `boNewDlgStyle` | Displays the dialog in the "new style" - i.e. the dialog is resizable and displays a "Make New Folder" button, by default. **Note:** This option is not compatible with `boShowHelp` and `boStatusText` and these options are ignored when `boNewDlgStyle` is included in _Options_. The option requires `shlobj.dll` v5.0 or later. |
| `boHideMakeFolderBtn` | Hides the "Make New Folder" button that is displayed by default in the "new style" dialog box. **Note:** This option is ignored if `boNewDlgStyle` is not set since the button is never displayed in "old style" versions of the dialog box. |
| `boEditBox` | Displays an edit control in the dialog box that allows the user to type the name of an item. The entered text is validated when the user presses _OK_. If valid the entered text is used as the name of the required folder. If the text is invalid the default action is for the dialog box to close and to ignore the entered text. To override this provide an _[OnValidationFailed](TPJBrowseDialogOnValidationFailed.md)_ event handler. **Note:** If this option is specified the `boHint` option is ignored. |
| `boHint` | Adds a usage hint to the dialog box, in place of any edit box. **Note:** `boNewDlgStyle` must be included in _Option_ for this option to work, and `boEditBox` must not be set. `boHint` requires `shlobj.dll` v6.0 or later. |

The default value of _Options_ is `[boContextHelp, boDirsOnly]`.