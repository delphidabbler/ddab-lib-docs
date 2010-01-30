#summary Description of the TPJAboutBoxDlg.HelpContext property.
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !HelpContext property =

*Project:* [AboutBoxComponent About Box Component].

*Unit:* _PJAbout_. 

*Class:* _[TPJAboutBoxDlg TPJAboutBoxDlg]_

{{{
property HelpContext: THelpContext;

type THelpContext = -MaxLongInt..MaxLongInt;
}}}

== Description ==

_!HelpContext_ stores the number of the help topic in the application's help file that is displayed when the F1 key is pressed. If _!HelpContext_ is 0 then no help topic is displayed.

The default value is 0.
