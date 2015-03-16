#summary Description of the TPJVCLMsgDlg.OffsetTop property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !OffsetTop property =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

*Class:* _[TPJVCLMsgDlg TPJVCLMsgDlg]_

{{{
property OffsetTop: Integer;
}}}

== Description ==

The effect of _!OffsetTop_ is determined by the value of the _[TPJVCLMsgDlgAlign Align]_ property as follows:

|| *_Align_ property value* || *Effect of _!OffsetTop_* ||
|| `mdaScreenOffset` || Sets vertical offset of dialogue box from top of screen. ||
|| `mdaScreenCentre` || No effect: property is ignored. ||
|| `mdaFormOffset` || Sets vertical offset of dialogue box from top of owning form. ||
|| `mdaFormCentre` || No effect: property is ignored.||

_!OffsetTop_ is used in conjunction with _[TPJVCLMsgDlgOffsetLeft OffsetLeft]_.

The default value of the property is 0.