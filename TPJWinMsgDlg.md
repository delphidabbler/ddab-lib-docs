#summary TPJWinMsgDlg class description
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= TPJWinMsgDlg =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

_TPJWinMsgDlg_ provides a customisable Windows message dialogue box. The component wraps the Windows _!MessageBoxIndirect_ API call. 

Its properties are a subset of those of _[TPJVCLMsgDlg TPJVCLMsgDlg]_. _TPJWinMsgDlg_ is recommended for new projects requiring a Windows message box. If even greater control over the appearance of the dialogue is required then use _[TPJVCLMsgDlg TPJVCLMsgDlg]_.

The text displayed in the dialogue box is determined by the _[TPJWinMsgDlgText Text]_ property. Various button groupings can be displayed using the _[TPJWinMsgDlgButtonGroup ButtonGroup]_ property. Setting a non-zero _[TPJWinMsgDlgHelpContext HelpContext]_ causes a help button to be displayed. The _[TPJWinMsgDlgKind Kind]_ property allows a choice of various standard windows icons to be displayed. A user defined icon extracted from a named resource, specified by _[TPJWinMsgDlgIconResource IconResource]_ can also be displayed. The window title can be set using the _[TPJWinMsgDlgTitle Title]_ property, otherwise a default title, related to the kind of icon being displayed is used. The _[TPJWinMsgDlgMakeSound MakeSound]_ property determines whether an appropriate system sound is generated when the dialogue is displayed.

== Methods ==

|| *Method* || *Description* ||
|| _[TPJWinMsgDlgExecute Execute]_ || Displays the dialogue box and returns information about the button pressed to close it. ||

== Properties ==

|| *Property* || *Description* ||
|| _[TPJWinMsgDlgButtonGroup ButtonGroup]_ || Determines which buttons appear in the dialogue box. ||
|| _[TPJWinMsgDlgDlgType DlgType]_ || Permits the buttons and type of dialogue box displayed to be specified by means of the flags that are passed to the _uType_ parameter of the Windows _!MessageBox_ API function. ||
|| _[TPJWinMsgDlgHelpContext HelpContext]_ || Specifies the context number for online help and displays a help button. ||
|| _[TPJWinMsgDlgHelpFile HelpFile]_ || Specifies the file to use for online help. ||
|| _[TPJWinMsgDlgIconResource IconResource]_ || Specifies the resource containing the dialogue box's icon. ||
|| _[TPJWinMsgDlgKind Kind]_ || Determines the type of dialogue box that is displayed. ||
|| _[TPJWinMsgDlgMakeSound MakeSound]_ || Flag that determines if a sound will be emitted when the dialogue box is displayed. ||
|| _[TPJWinMsgDlgText Text]_ || The text that is displayed in the dialogue box. ||
|| _[TPJWinMsgDlgTitle Title]_ || The dialogue box's window title. ||

== Events ==

|| *Event* || *Description* ||
|| _[TPJWinMsgDlgOnHelp OnHelp]_ || Event triggered when a user requests help in a dialogue box. ||