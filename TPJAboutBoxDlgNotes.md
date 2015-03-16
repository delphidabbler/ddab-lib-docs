#summary Description of the TPJAboutBoxDlg.Notes property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Notes property =

*Project:* [AboutBoxComponent About Box Component].

*Unit:* _PJAbout_. 

*Class:* _[TPJAboutBoxDlg TPJAboutBoxDlg]_

{{{
property Notes: string;
}}}

== Description ==

The _Notes_ property is used to store the notes to be displayed in the about box. The notes appear at the bottom of the text area. The text will word-wrap up to three lines. When setting the property at run time end of line characters can be included in the string to force line breaks.

The default value for this property is an empty string, which displays nothing. 

Note: If the _[TPJAboutBoxDlgVersionInfo VersionInfo]_ property is not nil then _Notes_ is ignored.
