# OnSelChangeEx event #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
type
  TPJBrowseSelChangeEventEx = procedure(Sender: TObject;
    PIDL: PItemIDList; var StatusText: AnsiString;
    var OKEnabled: Boolean) of object;

property OnSelChangeEx: TPJBrowseSelChangeEventEx;
```

## Description ##

This event is triggered whenever the selected folder in the dialog box changes. It provides access to the PIDL of the folder that has been selected. The event immediately follows the _[OnSelChange](TPJBrowseDialogOnSelChange.md)_ event and can occur before the dialog is displayed and before the _[OnInitialise](TPJBrowseDialogOnInitialise.md)_ event is triggered.  Write a handler to perform any required processing of the PIDL when the selected folder changes and to update the status text and state of the dialog's _OK_ button. It is recommended that only one of the _[OnSelChange](TPJBrowseDialogOnSelChange.md)_ and _OnSelChangeEx_ events is handled.

The event handler's parameters are as follows:

  * _Sender_ contains a reference to the _[TPJBrowseDialog](TPJBrowseDialog.md)_ component that triggered the event.
  * _PIDL_ is the PIDL of the newly selected folder. Note: This PIDL should be copied if it is to be retained beyond the life of the event handler and the copy should ultimately be freed using the Shell's allocator.
  * _StatusText_ will always be the empty string. Set this value to whatever text should be displayed in the dialog's status area. Setting _StatusText_ will only have an effect if the _[Options](TPJBrowseDialogOptions.md)_ property includes `boStatusText` and does not include `boNewDlgStyle`. Setting the status text in this event handler will override any status text set in the _[OnSelChange](TPJBrowseDialogOnSelChange.md)_ event handler.
  * _OKEnabled_ will be True if the dialog's _OK_ button is currently enabled and False if it is disabled. Setting _OKEnabled_ to a different value will change the state of the _OK_ button accordingly. The default state of the _OK_ button depends on whether `boDirsOnly` is included in the _[Options](TPJBrowseDialogOptions.md)_ property. If `boDirsOnly` is included in _[Options](TPJBrowseDialogOptions.md)_ then the _OK_ button will be enabled when a physical folder is selected and disabled when a virtual folder is selected.

When _OnSelChangeEx_ is triggered the dialog's window handle is available via the _[Handle](TPJBrowseDialogHandle.md)_ property.