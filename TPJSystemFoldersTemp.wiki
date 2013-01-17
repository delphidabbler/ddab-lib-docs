#summary Description of the TPJSystemFolders.Temp class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Temp class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJSystemFolders TPJSystemFolders]_

{{{
class function Temp: string;
}}}

== Description ==

Returns the fully qualified path name of the temporary files folder. This is the folder where programs are expected to create their temporary files.

On some Windows versions the folder may be different for each user.