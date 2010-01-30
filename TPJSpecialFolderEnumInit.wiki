#summary Description of the TPJSpecialFolderEnum.Init method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Init method =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Interface:* _[TPJSpecialFolderEnum TPJSpecialFolderEnum]_

{{{
procedure Init;
}}}

== Description ==

The _Init_ method initialises the enumeration so that the next call of the _[TPJSpecialFolderEnumNext Next]_ method returns the first special folder identifier value.

_Init_ is implicitly called by the constructor.
