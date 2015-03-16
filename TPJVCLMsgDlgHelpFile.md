#summary Description of the TPJVCLMsgDlg.HelpFile property
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= !HelpFile property =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

*Class:* _[TPJVCLMsgDlg TPJVCLMsgDlg]_

{{{
property HelpFile: string;
}}}

== Description ==

Set the _!HelpFile_ property to specify the help file to be used when a Help button is clicked or F1 is pressed in the dialogue. If _!HelpFile_ is set to the empty string then the help file associated with the parent form or application is used.

The _[TPJVCLMsgDlgHelpContext HelpContext]_ property is used to specify the help topic within the help file that is to be displayed. 

If _[TPJVCLMsgDlgOnHelp OnHelp]_ is not handled and a help button is pressed, a request is made to the _Application_ object to pass the value of this property and the _[TPJVCLMsgDlgHelpContext HelpContext]_ property along to the currently registered help system.