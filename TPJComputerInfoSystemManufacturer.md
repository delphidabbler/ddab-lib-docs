#summary Description of the TPJComputerInfo.SystemManufacturer class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !SystemManufacturer class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJComputerInfo TPJComputerInfo]_

*Introduced:* v4.0

{{{
class function SystemManufacturer: string;
}}}

== Description ==

Returns the name of the host computer's manufacturer.

The returned name does not include the computer's model (product) name. To get that, use the _[TPJComputerInfoSystemProductName SystemProductName]_ property.