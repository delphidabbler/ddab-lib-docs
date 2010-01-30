#summary Description of the TPJBrowseDialog.DisplayName property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !DisplayName property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
property DisplayName: string;
}}}

== Description ==

This property provides the display name of the folder the user selected or entered in the dialog box. This name is the same as that displayed in the dialog box. If the selected folder is a physical folder in the file system then _!DisplayName_ contains the name of the folder whose full path is specified in the _[TPJBrowseDialogFolderName FolderName]_ property. If the user cancelled the dialog box then _!DisplayName_ is not updated.

If _!DisplayName_ is set to the empty string then no folder has yet been selected by the user.

The property is run time and read only.

*See also:*
  * _[TPJBrowseDialogFolderName FolderName]_
