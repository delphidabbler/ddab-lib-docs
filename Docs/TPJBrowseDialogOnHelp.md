# OnHelp event #

**Project:** [Shell Folders Unit](ShellFoldersUnit.md).

**Unit:** _PJShellFolders_.

**Class:** _[TPJBrowseDialog](TPJBrowseDialog.md)_

```pascal
type
  TPJBrowseHelpEvent = procedure(Sender: TObject;
    var Cancel: Boolean) of object;

property OnHelp: TPJBrowseHelpEvent;
```

## Description ##

This event is triggered whenever help is requested and is available. Its purpose is to enable the user to intercept help requests before they are passed to the _Application_ object for processing and, optionally, to prevent _Application_ from receiving the request.

Help can be requested by clicking any visible and enabled help button or by pressing F1 whenever `boContextHelp` is not included in the _[Options](TPJBrowseDialogOptions.md)_ property.  Help is available when either _[HelpContext](TPJBrowseDialogHelpContext.md)_ is non-zero or _[HelpKeyword](TPJBrowseDialogHelpKeyword.md)_ is not the empty string, depending on the value of the _[HelpType](TPJBrowseDialogHelpType.md)_ property. (On Delphis that don't support _[HelpType](TPJBrowseDialogHelpType.md)_, _[HelpContext](TPJBrowseDialogHelpContext.md)_ must be non-zero).

The event handler's parameters are described below:

  * _Sender_ provides a reference to the calling component and can be cast to _[TPJBrowseDialog](TPJBrowseDialog.md)_ to gain access to the _[HelpContext](TPJBrowseDialogHelpContext.md)_, _[HelpKeyword](TPJBrowseDialogHelpKeyword.md)_ and _[HelpType](TPJBrowseDialogHelpType.md)_ properties.
  * _Cancel_ is false when the event handler is called which means the help request will be passed to the _Application_ object. To prevent this set _Cancel_ to true.