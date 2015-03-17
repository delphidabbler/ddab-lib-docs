# OnValidationFailed event #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
type
  TPJBrowseValidationFailedEvent = procedure(Sender: TObject;
    const EditText: string; var CanClose: Boolean) of object;

property OnValidationFailed: TPJBrowseValidationFailedEvent;
```

## Description ##

_OnValidationFailed_ is triggered whenever an invalid folder is entered in the browser dialog's edit control and the user OKs. The event is only ever triggered if the _[Options](TPJBrowseDialogOptions.md)_ property contains both the `boNewDlgStyle` and `boEditBox` options.

The event handler's parameters are:

  * _Sender_ contains a reference to the [dialog box component](TPJBrowseDialog.md) that triggers the event.
  * _EditText_ contains the erroneous text entered in the edit control.
  * _CanClose_ indicates whether the dialog box is permitted to close: it is true when the event is triggered but can be changed to False in the event handler to prevent the dialog box from closing.

Implement an event handler to take any required action, such as displaying an error message.