#summary Description of the TPJComputerInfo.IsAdmin class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IsAdmin class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJComputerInfo TPJComputerInfo]_

*Introduced:* v4.0

{{{
class function IsAdmin: Boolean;
}}}

== Description ==

Checks if the current user has administrator privileges and returns True if so, or False if not.

True is always returned on the Windows 95 platform, since there is no real concept of "administrator" on the platform.

*WARNING:* If the program is running on a Windows NT platform operating system in Windows 9x compatibility mode, _!IsAdmin_ will always return True regardless of whether the user actually has admin privileges or not.