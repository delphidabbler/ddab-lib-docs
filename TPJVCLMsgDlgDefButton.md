#summary Description of the TPJVCLMsgDlg.DefButton property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !DefButton property =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

*Class:* _[TPJVCLMsgDlg TPJVCLMsgDlg]_

{{{
type
  TMsgDlgButton = (
    mbYes, mbNo, mbOK, mbCancel, mbAbort, mbRetry, mbIgnore,
    mbAll, mbNoToAll, mbYesToAll, mbHelp, mbClose
  );

property DefButton: TMsgDlgButton;
}}}

== Description ==

The _!DefButton_ property specifies which button is to be the default button in the dialogue. If the chosen button is not displayed in the dialogue then the first (leftmost) button is the default.

See the documentation of the _[TPJVCLMsgDlgButtons Buttons]_ property for a description of the available buttons.

The default value of the property is `mbOK`.
