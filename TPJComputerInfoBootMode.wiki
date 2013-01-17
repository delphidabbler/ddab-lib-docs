#summary Description of the TPJComputerInfo.BootMode class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !BootMode class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJComputerInfo TPJComputerInfo]_

*Introduced:* v3.1

{{{
class function BootMode: TPJBootMode;

type TPJBootMode = (bmUnknown, bmNormal, bmSafeMode, bmSafeModeNetwork);
}}}

== Description ==

Determines the operating system mode into which the the computer was booted.

Returns a value from the _TPJBootMode_ enumeration that describes the boot mode. Values of _TPJBootMode_ are:

|| `bmUnknown` || Unknown boot mode. ||
|| `bmNormal` || Normal boot. ||
|| `bmSafeMode` || Booted in safe mode with no networking. ||
|| `bmSafeModeNetwork` || Booted in safe mode with networking. ||