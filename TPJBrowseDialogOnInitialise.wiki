#summary Description of the TPJBrowseDialog.OnInitialise event.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OnInitialise event =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
property OnInitialise: TNotifyEvent;
}}}

== Description ==

_!OnInitialise_ occurs when the dialog initialises.

This event is triggered after the dialog has opened and the default folder has been selected but before the dialog is displayed. Because of this the _[TPJBrowseDialogOnSelChange OnSelChange]_ and _[TPJBrowseDialogOnSelChangeEx OnSelChangeEx]_ events will usually fire before _!OnInitialise_. The dialog's window handle is available via the _[TPJBrowseDialogHandle Handle]_ property.

Write an _!OnInitialise_ event handler to perform special processing when the dialog is intialised.
