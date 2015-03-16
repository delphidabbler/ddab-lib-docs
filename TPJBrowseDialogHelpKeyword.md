#summary Description of the TPJBrowseDialog.HelpKeyword property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !HelpKeyword property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
property HelpKeyword: string;
}}}

== Description ==

_!HelpKeyword_ contains a keyword keyword that determines which help topic appears when the user requests help. _!HelpKeyword_ has effect only if the following conditions are met:

  * The _[TPJBrowseDialogHelpType HelpType]_ property is set to `htKeyword`.
  * The dialog's help button is displayed, enabled and is clicked.
  * The F1 key if pressed and the _[TPJBrowseDialogOptions Options]_ property does not include `boContextHelp`.

If _!HelpKeyword_ is set to the default value of the empty string, and _[TPJBrowseDialogHelpType HelpType]_ = `htKeyword` then any help button that is displayed is disabled.

*Note:* This property is only available when the unit is compiled with Delphi 6 or later.
