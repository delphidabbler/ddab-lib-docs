#summary Description of the TPJAboutBoxDlg.Version property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Version property =

*Project:* [AboutBoxComponent About Box Component].

*Unit:* _PJAbout_. 

*Class:* _[TPJAboutBoxDlg TPJAboutBoxDlg]_

{{{
property Version: string;
}}}

== Description ==

The _Version_ property defines the version number (or other text) to appear on the second line of the about box.

The default value of this property is an empty string, which displays nothing.

Note: If the _[TPJAboutBoxDlgVersionInfo VersionInfo]_ property is not nil then _Version_ is ignored.
