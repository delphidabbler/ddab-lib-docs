#summary Description of the TPJSystemFolders.CommonFiles class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !CommonFiles class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJSystemFolders TPJSystemFolders]_

{{{
class function CommonFiles: string;
}}}

== Description ==

Returns the fully qualified path name of the Common Files folder. This is usually a sub-folder of the Program Files folder.

On 64 bit Windows, both 32 bit and 64 bit programs will report the same value, i.e. the value used for "native" 64 bit programs.

*See also*

  * _[TPJSystemFoldersCommonFilesX86 CommonFilesX86]_
  * _[TPJSystemFoldersCommonFilesRedirect CommonFilesRedirect]_