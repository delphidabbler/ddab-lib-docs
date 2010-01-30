#summary Description of the TPJAboutBoxDlg.DlgLeft property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !DlgLeft property =

*Project:* [AboutBoxComponent About Box Component].

*Unit:* _PJAbout_. 

*Class:* _[TPJAboutBoxDlg TPJAboutBoxDlg]_

{{{
property DlgLeft: Integer;
}}}

== Description ==

The _!DlgLeft_ property determines the position of the left hand side of the about dialog box in pixels. Whether the left side of the dialog is aligned relative to the screen, the desktop work area or the owning control depends on the value of the _[TPJAboutBoxDlgPosition Position]_ property. The alignment may be adjusted to ensure the whole of the dialog can be seen.

If the _[TPJAboutBoxDlgCentreDlg CentreDlg]_ property is true then _!DlgLeft_ is ignored and the dialog is centred.

The default value is 0.
