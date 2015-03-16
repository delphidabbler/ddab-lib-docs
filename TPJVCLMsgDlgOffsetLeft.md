#summary Description of the TPJVCLMsgDlg.OffsetLeft property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OffsetLeft property =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

*Class:* _[TPJVCLMsgDlg TPJVCLMsgDlg]_

{{{
property OffsetLeft: Integer;
}}}

== Description ==

The effect of _!OffsetLeft_ is determined by the value of the _[TPJVCLMsgDlgAlign Align]_ property as follows:

|| *_Align_ property value* || *Effect of _!OffsetLeft_* ||
|| `mdaScreenOffset` || Sets horizontal offset of dialogue box from left hand side of screen. ||
|| `mdaScreenCentre` || No effect: property is ignored. ||
|| `mdaFormOffset` || Sets horizontal offset of dialogue box from left hand side of owning form. ||
|| `mdaFormCentre` || No effect: property is ignored.||

_!OffsetLeft_ is used in conjunction with _[TPJVCLMsgDlgOffsetTop OffsetTop]_.

The default value of the property is 0.