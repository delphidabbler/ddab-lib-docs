#summary Description of the TPJBrowseDialog.HelpContext property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !HelpContext property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
type
  THelpContext = -MaxLongInt..MaxLongInt;

property HelpContext: THelpContext;
}}}

== Description ==

This property contains an integer value that determines which help topic appears when the user requests help. _!HelpContext_ has effect only if the following conditions are met:

  * The _[TPJBrowseDialogHelpType HelpType]_ property is set to `htContext`. (Delphi 6 and later only).
  * The dialog's help button is displayed, enabled and is clicked.
  * The F1 key if pressed and the _[TPJBrowseDialogOptions Options]_ property does not include `boContextHelp`.

If _!HelpContext_ is set to the default value of 0, and _[TPJBrowseDialogHelpType HelpType]_ = `htContext` then any help button that is displayed is disabled.
