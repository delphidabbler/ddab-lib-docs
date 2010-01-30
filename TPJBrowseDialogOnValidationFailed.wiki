#summary Description of the TPJBrowseDialog.OnValidationFailed event.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnValidationFailed event =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
type
  TPJBrowseValidationFailedEvent = procedure(Sender: TObject;
    const EditText: string; var CanClose: Boolean) of object;

property OnValidationFailed: TPJBrowseValidationFailedEvent;
}}}

== Description ==

_!OnValidationFailed_ is triggered whenever an invalid folder is entered in the browser dialog's edit control and the user OKs. The event is only ever triggered if the _[TPJBrowseDialogOptions Options]_ property contains both the `boNewDlgStyle` and `boEditBox` options.

The event handler's parameters are:

  * _Sender_ contains a reference to the [TPJBrowseDialog dialog box component] that triggers the event.
  * _!EditText_ contains the erroneous text entered in the edit control.
  * _!CanClose_ indicates whether the dialog box is permitted to close: it is true when the event is triggered but can be changed to False in the event handler to prevent the dialog box from closing.
  
Implement an event handler to take any required action, such as displaying an error message.
