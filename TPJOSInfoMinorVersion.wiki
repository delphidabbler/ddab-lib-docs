#summary Description of the TPJOSInfo.MinorVersion class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !MinorVersion class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJOSInfo TPJOSInfo]_

{{{
class function MinorVersion: Integer;
}}}

== Description ==

Returns the minor version number of the operating system.

The corresponding major version number is provided by the _[TPJOSInfoMajorVersion MajorVersion]_ method.

When the program is run in compatibility mode, this method will return the minor version number of the "emulated" operating system.

[v5.0] On operating systems where _[TPJOSInfoCanSpoof CanSpoof]_ returns `False` this method will return the minor version number of the installed operating system, regardless of any compatibility mode.