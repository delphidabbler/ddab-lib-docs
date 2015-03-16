#summary Description of the TPJOSInfo.MajorVersion class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !MajorVersion class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJOSInfo TPJOSInfo]_

{{{
class function MajorVersion: Integer;
}}}

== Description ==

Returns the major version number of the operating system.

The corresponding minor version number is provided by the _[TPJOSInfoMinorVersion MinorVersion]_ method.

When the program is run in compatibility mode, this method will return the major version number of the "emulated" operating system.

[v5.0] On operating systems where _[TPJOSInfoCanSpoof CanSpoof]_ returns `False` this method will return the major version number of the installed operating system, regardless of any compatibility mode.