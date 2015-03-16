#summary Description of the TPJComputerInfo.ProcessorIdentifier class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ProcessorIdentifier class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJComputerInfo TPJComputerInfo]_

*Introduced:* v4.0

{{{
class function ProcessorIdentifier: string;
}}}

== Description ==

Returns the identifier of the computer's processor.

On multi-processor systems the method returns the identifier of the 1st processor.

An example processor identifier is "`Intel64 Family 6 Model 58 Stepping 9`".

*See also*

  * _[TPJComputerInfoProcessorName ProcessorName]_