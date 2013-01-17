#summary Description of the TPJComputerInfo.ProcessorName class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ProcessorName class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJComputerInfo TPJComputerInfo]_

*Introduced:* v4.0

{{{
class function ProcessorName: string;
}}}

== Description ==

Returns a descriptive name for the computer's processor.

On multi-processor systems the method returns the name of the 1st processor.

An example processor name is "`Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz`".

*See also*

  * _[TPJComputerInfoProcessorIdentifier ProcessorIdentifier]_