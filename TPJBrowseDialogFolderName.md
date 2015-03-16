#summary Description of the TPJBrowseDialog.FolderName property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !FolderName property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJBrowseDialog TPJBrowseDialog]_

{{{
property FolderName: string;
}}}

== Description ==

This property contains the path to the folder selected in the dialog box.

Set _!FolderName_ to the path of the (physical) folder you would like to be selected in the dialog box when it is displayed.

When the user OKs the dialog box _!FolderName_ is updated. For physical folders (i.e. those in the file system) this property contains the full path name of the folder that was selected by the user in the dialog box. If the selected folder is virtual then this property is set to the empty string. If the user cancelled the dialog box then _!FolderName_ is not updated.

_!FolderName_ is set to the empty string when no folder has yet been selected by the user.

*See also:*
  * _[TPJBrowseDialogDisplayName DisplayName]_
