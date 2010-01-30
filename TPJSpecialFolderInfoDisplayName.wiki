#summary Description of the TPJSpecialFolderInfo.DisplayName property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !DisplayName property =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Class:* _[TPJSpecialFolderInfo TPJSpecialFolderInfo]_

{{{
property DisplayName: string;
}}}

== Description ==

This property gives the display name of the special folder specified by the _[TPJSpecialFolderInfoFolderID FolderID]_ property. For physical folders (_[TPJSpecialFolderInfoIsVirtual IsVirtual]_ is false), _!DisplayName_ often (but not always) has the same value as the _[TPJSpecialFolderInfoPath Path]_ property.

_!DisplayName_ is set to the empty string if the special folder is not supported by the operating system (see _[TPJSpecialFolderInfoIsSupported IsSupported]_).
