#summary Description of the TPJOSInfo.BuildNumber class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !BuildNumber class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJOSInfo TPJOSInfo]_

{{{
class function BuildNumber: Integer;
}}}

== Description ==

Returns the build number of the operating system.

When the program is run in compatibility mode, this method will return the build number of the "emulated" operating system.

[v5.0] On operating systems where _[TPJOSInfoCanSpoof CanSpoof]_ returns `False` this method will return the build number of the installed operating system, regardless of any compatibility mode.