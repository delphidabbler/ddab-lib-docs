#summary Description of the TPJSystemFolders.ProgramFiles class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ProgramFiles class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJSystemFolders TPJSystemFolders]_

{{{
class function ProgramFiles: string;
}}}

== Description ==

Returns the fully qualified path name of the system's Program Files folder.

On 64 bit Windows, both 32 bit and 64 bit programs will report the same value, i.e. the value used for "native" 64 bit programs.

*See also*

  * _[TPJSystemFoldersProgramFilesX86 ProgramFilesX86]_
  * _[TPJSystemFoldersProgramFilesRedirect ProgramFilesRedirect]_