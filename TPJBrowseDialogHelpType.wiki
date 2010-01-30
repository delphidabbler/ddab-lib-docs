#summary Description of the TPJBrowseDialog.HelpType property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !HelpType property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
type
  THelpType = (htKeyword, htContext);

property HelpType: THelpType;
}}}

== Description ==

This property determines whether the _[TPJBrowseDialogHelpContext HelpContext]_ or _[TPJBrowseDialogHelpKeyword HelpKeyword]_ properties are used to identify the associated help topic.

When _!HelpType_ = `htKeyword`, the _[TPJBrowseDialogHelpKeyword HelpKeyword]_ property is used and _[TPJBrowseDialogHelpContext HelpContext]_ is ignored. Conversely when _!HelpType_ = `htContext`, _[TPJBrowseDialogHelpContext HelpContext]_ is used and _[TPJBrowseDialogHelpKeyword HelpKeyword]_ is ignored.

*Note:* This property is only available when the unit is compiled with Delphi 6 or later.
