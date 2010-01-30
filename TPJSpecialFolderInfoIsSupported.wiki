#summary Description of the TPJSpecialFolderInfo.IsSupported property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IsSupported property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJSpecialFolderInfo TPJSpecialFolderInfo]_

{{{
property IsSupported: Boolean;
}}}

== Description ==

Use _!IsSupported_ to determine if the current special folder is supported by the operating system.

This property returns true if the special folder specified by _[TPJSpecialFolderInfoFolderID FolderID]_ is supported on the operating system and false if it is not. When _!IsSupported_ is false the component's other properties have zero values: _[TPJSpecialFolderInfoIsVirtual IsVirtual]_ is false and _[TPJSpecialFolderInfoDisplayName DisplayName]_ and _[TPJSpecialFolderInfoPath Path]_ are empty strings.
