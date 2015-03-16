#summary Description of the TPJBrowseDialog.Handle property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Handle property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
property Handle: THandle;
}}}

== Description ==

This property provides access to the _Browse for Folder_ dialog box's window handle while the _[TPJBrowseDialogExecute Execute]_ method is active. At other times _Handle_ is set to 0. _Handle_ therefore only references a valid window handle when the dialog box is displayed.

_Handle_ is intended for use in the _[TPJBrowseDialogOnInitialise OnInitialise]_, _[TPJBrowseDialogOnSelChange OnSelChange]_, _[TPJBrowseDialogOnSelChangeEx OnSelChangeEx]_, _[TPJBrowseDialogOnValidationFailed OnValidationFailed]_ and _[TPJBrowseDialogOnClose OnClose]_ events whenever it is necessary to customise the window's behaviour.
