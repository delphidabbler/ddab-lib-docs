#summary Description of the TPJBrowseDialog.OnHelp event.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnHelp event =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
type
  TPJBrowseHelpEvent = procedure(Sender: TObject;
    var Cancel: Boolean) of object;

property OnHelp: TPJBrowseHelpEvent;
}}}

== Description ==

This event is triggered whenever help is requested and is available. Its purpose is to enable the user to intercept help requests before they are passed to the _Application_ object for processing and, optionally, to prevent _Application_ from receiving the request.

Help can be requested by clicking any visible and enabled help button or by pressing F1 whenever `boContextHelp` is not included in the _[TPJBrowseDialogOptions Options]_ property.  Help is available when either _[TPJBrowseDialogHelpContext HelpContext]_ is non-zero or _[TPJBrowseDialogHelpKeyword HelpKeyword]_ is not the empty string, depending on the value of the _[TPJBrowseDialogHelpType HelpType]_ property. (On Delphis that don't support _[TPJBrowseDialogHelpType HelpType]_, _[TPJBrowseDialogHelpContext HelpContext]_ must be non-zero).

The event handler's parameters are described below:

  * _Sender_ provides a reference to the calling component and can be cast to _[TPJBrowseDialog TPJBrowseDialog]_ to gain access to the _[TPJBrowseDialogHelpContext HelpContext]_, _[TPJBrowseDialogHelpKeyword HelpKeyword]_ and _[TPJBrowseDialogHelpType HelpType]_ properties.
  * _Cancel_ is false when the event handler is called which means the help request will be passed to the _Application_ object. To prevent this set _Cancel_ to true.
