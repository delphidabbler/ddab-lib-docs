#summary Description of the TPJComputerInfo.ProcessorCount class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ProcessorCount class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJComputerInfo TPJComputerInfo]_

{{{
class function ProcessorCount: Integer;
}}}

== Description ==

Returns the number of processors installed in the computer. Mutli-core processors will report each core as a separate processor.
