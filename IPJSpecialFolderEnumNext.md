#summary Description of the IPJSpecialFolderEnum.Next method.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Next method =

*Project:* [ShellFoldersUnit Shell Folders Unit].

*Unit:* _PJShellFolders_. 

*Interface:* _[IPJSpecialFolderEnum IPJSpecialFolderEnum]_

{{{
function Next: Integer;
}}}

== Description ==

The _Next_ method returns the value of the next special folder in the enumeration. If _Next_ is called when the enumeration is at an end then -1 is returned. To reinitialise the enumeration call _[IPJSpecialFolderEnumInit Init]_.
