#summary Description of the TPJWinMsgDlg.MakeSound property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !MakeSound property =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

*Class:* _[TPJWinMsgDlg TPJWinMsgDlg]_

{{{
property MakeSound: Boolean;
}}}

== Description ==

Set _!MakeSound_ to `True` to play a sound when the dialogue is displayed. If _!MakeSound_ is `False` then no sound is played.

The sound played is one of the standard system sounds. Which sound is used depends on the value of the _[TPJWinMsgDlgKind Kind]_ property, the operating system version and the chosen sound theme. Some themes will play no sound for some values of the _[TPJWinMsgDlgKind Kind]_ property regardless of the value assigned to _!MakeSound_.

The property's default value is `False`.