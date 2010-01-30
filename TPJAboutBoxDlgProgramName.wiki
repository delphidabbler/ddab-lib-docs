#summary Description of the TPJAboutBoxDlg.ProgramName property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !ProgramName property =

*Project:* [AboutBoxComponent About Box Component].

*Unit:* _PJAbout_. 

*Class:* _[TPJAboutBoxDlg TPJAboutBoxDlg]_

{{{
property ProgramName: string;
}}}

== Description ==

The _!ProgramName_ property defines the program name to be displayed on the first line of the about box.

If _!ProgramName_ is set to the empty string then the title of the application as specified by the _Title_ property of the _Application_ object is displayed. If you have not specified an application title then the name of the project (without the `.dpr` extension) is used. If _!ProgramName_ is set to any non-empty string then that string is displayed.

_!ProgramName_ defaults to the empty string.

Note: If the _[TPJAboutBoxDlgVersionInfo VersionInfo]_ property is not nil then _!ProgramName_ is ignored.
