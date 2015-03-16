#summary Description of the TPJOSInfo.InstallationDate class function.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !InstallationDate class function =

*Project:* [SystemInformationUnit System Information Unit].

*Unit:* _PJSysInfo_.

*Class:* _[TPJOSInfo TPJOSInfo]_

*Introduced:* v5.0 

{{{
class function InstallationDate: TDateTime;
}}}

== Description ==

Returns the date the operating system was installed if known.

If the installation date is not known then `0.0` is returned. This is the date code for 30 December 1899.