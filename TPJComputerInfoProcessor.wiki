#summary Description of the TPJComputerInfo.Processor class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Processor class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJComputerInfo TPJComputerInfo]_

{{{
class function Processor: TPJProcessorArchitecture;

type TPJProcessorArchitecture = (paUnknown, paX64, paIA64, paX86);
}}}

== Description ==

Returns a value from the _TPJProcessorArchitecture_ enumeration that describes the type of processor installed in the computer. Values of TPJProcessorArchitecture are:

|| `paUnknown` || Unknown processor. ||
|| `paX64` || X64 (AMD or Intel). ||
|| `paIA64` || Intel Itanium processor family. ||
|| `paX86` || Intel 32 bit x86. ||
