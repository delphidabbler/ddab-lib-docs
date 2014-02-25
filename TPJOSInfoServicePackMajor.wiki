#summary Description of the TPJOSInfo.ServicePackMajor class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ServicePackMajor class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJOSInfo TPJOSInfo]_

{{{
class function ServicePackMajor: Integer;
}}}

== Description ==

On the NT platform from NT 4 service pack 6 onwards _!ServicePackMajor_ returns the major version number of any service pack applied to the operating system. Zero is returned if no service pack has been applied. On earlier versions of Windows NT or on the Windows 9x platform, zero is alwys returned.

The corresponding minor service pack version number is provided by the _[TPJOSInfoServicePackMinor ServicePackMinor]_ method. A full description of the service pack, for any product, is available via the _[TPJOSInfoServicePack ServicePack]_ method.

When the program is run in compatibility mode, this method will return the service pack major version of the "emulated" operating system.

[v5.0] On operating systems where _[TPJOSInfoCanSpoof CanSpoof]_ returns `False` this method will return the service pack major version of the installed operating system, regardless of any compatibility mode.