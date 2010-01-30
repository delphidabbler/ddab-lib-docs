#summary Description of the TPJSpecialFolderInfo.IsVirtual property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IsVirtual property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJSpecialFolderInfo TPJSpecialFolderInfo]_

{{{
property IsVirtual: Boolean;
}}}

== Description ==

Use _!IsVirtual_ to determine if the current special folder is virtual or not.

When the property is false the special folder specified by _[TPJSpecialFolderInfoFolderID FolderID]_ the folder is a physical folder in the file system and the _[TPJSpecialFolderInfoPath Path]_ property gives its location. When _!IsVirtual_ is true then the folder is not physically present in the file system and the _[TPJSpecialFolderInfoPath Path]_ property is set to the empty string.

_!IsVirtual_ is set to false if the special folder is not supported by the operating system (see _[TPJSpecialFolderInfoIsSupported IsSupported]_).
