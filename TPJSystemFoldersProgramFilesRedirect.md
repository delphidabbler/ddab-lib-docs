#summary Description of the TPJSystemFolders.ProgramFilesRedirect class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ProgramFilesRedirect class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJSystemFolders TPJSystemFolders]_

*Introduced:* v4.0

{{{
class function ProgramFilesRedirect: string;
}}}

== Description ==

Returns the fully qualified path name of the Program Files folder, taking into account any redirection for 32 bit programs running on 64 bit Windows.

The return value will be the same as one of the _[TPJSystemFoldersProgramFiles ProgramFiles]_ or _[TPJSystemFoldersProgramFilesX86 ProgramFilesX86]_ methods as follows:

|| Operating System || Application || Return Value ||
|| 32 bit Windows || 32 bit || _[TPJSystemFoldersProgramFiles ProgramFiles]_ ||
|| 64 bit Windows || 32 bit || _[TPJSystemFoldersProgramFilesX86 ProgramFilesX86]_ ||
|| 64 bit Windows || 64 bit || _[TPJSystemFoldersProgramFiles ProgramFiles]_ ||

*See also*
  * _[TPJSystemFoldersProgramFiles ProgramFiles]_
  * _[TPJSystemFoldersProgramFilesX86 ProgramFilesX86]_