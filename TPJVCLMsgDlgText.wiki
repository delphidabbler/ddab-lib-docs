#summary Description of the TPJVCLMsgDlg.Text property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= Text property =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

*Class:* _[TPJVCLMsgDlg TPJVCLMsgDlg]_

{{{
property Text: string;
}}}

== Description ==

Set this property to the text that you wish to display in the body on the dialogue box. The default is to display nothing.

*Note:* Line breaks in the dialogue box can be forced by including CR LF pairs in the _Text_ string. This can't be done at design time using the standard Delphi string property editor. However the !DelphiDabbler [ExStringPropertyEditor Extended String Property Editor] enables multiple lines of text to be assigned at design time.