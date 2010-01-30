#summary Description of the TPJOSInfo.IsWin32s class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !IsWin32s class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJOSInfo TPJOSInfo]_

{{{
class function IsWin32s: Boolean;
}}}

== Description ==

Returns True if running on the Win32s subsystem or False if not. This is unlikely to ever return true since Delphi does not run on Win32s.
