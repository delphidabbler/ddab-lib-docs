# OnSelChange event #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
type
  TPJBrowseSelChangeEvent = procedure(Sender: TObject; 
    FolderName, DisplayName: AnsiString; var StatusText: AnsiString;
    var OKEnabled: Boolean) of object;

property OnSelChange: TPJBrowseSelChangeEvent;
```

## Description ##

_OnSelChange_ is triggered whenever the selection in the dialog box changes. This can occur before the dialog is displayed and before the _[OnInitialise](TPJBrowseDialogOnInitialise.md)_ event fires.  Write a handler to perform any required processing when the selected folder changes and to update the status text and state of the dialog's _OK_ button. The _OnSelChange_ event is immediately followed by the _[OnSelChangeEx](TPJBrowseDialogOnSelChangeEx.md)_ event. It is recommended that only one of these events is handled.

The event handler's parameters are as follows:

  * _Sender_ contains a reference to the _[TPJBrowseDialog](TPJBrowseDialog.md)_ component that triggered the event.
  * _FolderName_ is the full path name name of newly selected folder (or the empty string if the folder is virtual).
  * _DisplayName_ is the text used to display the newly selected folder in the dialog's tree view.
  * _StatusText_ will always be the empty string. Set this value to whatever text should be displayed in the dialog's status area. Setting _StatusText_ will only have an effect if the _[Options](TPJBrowseDialogOptions.md)_ property includes `boStatusText` and does not include `boNewDlgStyle`.
  * _OKEnabled_ will be True if the dialog's _OK_ button is currently enabled and False if it should be disabled. Setting _OKEnabled_ to a different value will change the state of the _OK_ button accordingly. The default state of the _OK_ button depends on whether `boDirsOnly` is included in the _[Options](TPJBrowseDialogOptions.md)_ property. If `boDirsOnly` is included in _[Options](TPJBrowseDialogOptions.md)_ then the _OK_ button will be enabled when a physical folder is selected and disabled when a virtual folder is selected.

When _OnSelChange_ is triggered the dialog's window handle is available via the _[Handle](TPJBrowseDialogHandle.md)_ property.