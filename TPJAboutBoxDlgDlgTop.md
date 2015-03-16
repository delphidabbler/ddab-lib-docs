#summary Description of the TPJAboutBoxDlg.DlgTop property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !DlgTop property =

*Project:* [AboutBoxComponent About Box Component].

*Unit:* _PJAbout_. 

*Class:* _[TPJAboutBoxDlg TPJAboutBoxDlg]_

{{{
property DlgTop: Integer;
}}}

== Description ==

The _!DlgTop_ property determines the position of the top of the about dialog box in pixels. Whether the top of the dialog is aligned relative to the screen, the desktop work area or the owning control depends on the value of the _[TPJAboutBoxDlgPosition Position]_ property. The alignment may be adjusted to ensure the whole of the dialog can be seen.

If the _[TPJAboutBoxDlgCentreDlg CentreDlg]_ property is true then _!DlgTop_ is ignored and the dialog is centred.

The default value is 0.
