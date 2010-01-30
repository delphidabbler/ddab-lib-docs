#summary Description of the TPJBrowseDialog.OnClose event.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnClose event =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
property OnClose: TNotifyEvent;
}}}

== Description ==

This event occurs when the dialog closes.

Write an _!OnClose_ event handler to perform special processing when the dialog closes.

The dialog's window handle is available via the _[TPJBrowseDialogHandle Handle]_ property. The _Sender_ parameter can be cast to _[TPJBrowseDialog TPJBrowseDialog]_ in order to access the _[TPJBrowseDialogHandle Handle]_ property.
