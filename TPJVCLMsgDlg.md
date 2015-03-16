#summary TPJVCLMsgDlg class description
<wiki:comment>
$Rev$
$Date$
</wiki:comment>

= TPJVCLMsgDlg =

*Project:* [MessageDialogComponents Message Dialogue Components].

*Unit:* _PJMessageDialog_.

_TPJVCLMsgDlg_ provides a customisable message dialogue box that is based on that provided by the Delphi _!CreateMessageDialog_ function. The component provides a similar (but extended) interface to the _[TPJWinMsgDlg TPJWinMsgDlg]_ component but uses a different method to display the dialogue box. This component is recommended when a finer degree of control to that provided by _[TPJWinMsgDlg TPJWinMsgDlg]_ is required.

The text displayed in the dialogue box is determined by the _[TPJVCLMsgDlgText Text]_ property. Various button groupings can be displayed using the _[TPJVCLMsgDlgButtonGroup ButtonGroup]_ and/or _[TPJVCLMsgDlgButtons  Buttons]_ properties. Setting a non-zero _[TPJVCLMsgDlgHelpContext HelpContext]_ causes a help button to be displayed. The _[TPJVCLMsgDlgKind Kind]_ property allows a choice of various standard dialogue boxes and icons to be displayed. A user defined icon extracted from a named resource, specified by _[TPJVCLMsgDlgIconResource IconResource]_ can also be displayed. The window title can be customised using the _[TPJVCLMsgDlgTitle Title]_ property, otherwise a default title is used that is related to the kind of icon being displayed. The _[TPJVCLMsgDlgMakeSound MakeSound]_ property determines whether an appropriate system sound is generated when the dialogue is displayed. It is possible to set how the dialogue box is to be aligned to screen or form using the _[TPJVCLMsgDlgAlign  Align]_ property in combination with the _[TPJVCLMsgDlgOffsetLeft OffsetLeft]_ and _[TPJVCLMsgDlgOffsetTop OffsetTop]_ properties.

The dialogue box can be invoked with the _[TPJVCLMsgDlgExecute Execute]_ method or an instance of the dialogue can be created using the _[TPJVCLMsgDlgCreateDialog CreateDialog]_ method. In the latter case the user has responsibility for showing and hiding the dialogue and destroying the instance.

== Methods ==

|| *Method* || *Description* ||
|| _[TPJVCLMsgDlgCreateDialog CreateDialog]_ || Creates instance of  the dialogue box and returns a reference to it. ||
|| _[TPJVCLMsgDlgExecute Execute]_ || Displays the dialogue box and returns information about the button pressed to close it. ||

== Properties ==

|| *Property* || *Description* ||
|| _[TPJVCLMsgDlgAlign Align]_ || Determines the on screen alignment of the dialogue box. ||
|| _[TPJVCLMsgDlgButtonGroup ButtonGroup]_ || Determines which buttons appear in the dialogue box. ||
|| _[TPJVCLMsgDlgButtons Buttons]_ || Determines the buttons displayed in the dialogue box . Provides finer control than _[TPJVCLMsgDlgButtonGroup ButtonGroup]_. ||
|| _[TPJVCLMsgDlgDefButton DefButton]_ || Determines the default button in the dialogue box. ||
|| _[TPJVCLMsgDlgDlgType DlgType]_ || Permits the buttons and type of dialogue box displayed to be specified by means of the flags that are passed to the _uType_ parameter of the Windows _!MessageBox_ API function. ||
|| _[TPJVCLMsgDlgHelpContext HelpContext]_ || Specifies the context number for online help. ||
|| _[TPJVCLMsgDlgHelpFile HelpFile]_ || Specifies the file to use for online help. ||
|| _[TPJVCLMsgDlgIconResource IconResource]_ || Specifies the resource containing the dialogue box's icon. ||
|| _[TPJVCLMsgDlgKind Kind]_ || Determines the type of  dialogue box that is displayed. ||
|| _[TPJVCLMsgDlgMakeSound MakeSound]_ || Flag that determines if a sound will be emitted when the dialogue box is displayed. ||
|| _[TPJVCLMsgDlgOffsetLeft OffsetLeft]_ || Determines the offset of the dialogue box from the left of the screen or owning form. ||
|| _[TPJVCLMsgDlgOffsetTop OffsetTop]_ || Determines the offset of the dialogue box from the top of the screen or owning form. ||
|| _[TPJVCLMsgDlgOptions Options]_ || Property that records various customisation options. ||
|| _[TPJVCLMsgDlgText Text]_ || The text that is displayed in the dialogue box. ||
|| _[TPJVCLMsgDlgTitle Title]_ || The dialogue box's window title. ||

== Events ==

|| *Event* || *Description* ||
|| _[TPJVCLMsgDlgOnHelp OnHelp]_ || Event triggered when a user requests help in a dialogue box. ||
|| _[TPJVCLMsgDlgOnHide OnHide]_ || Event triggered just after the component's dialogue box is hidden. ||
|| _[TPJVCLMsgDlgOnShow OnShow]_ || Event triggered just before the component's dialogue box is displayed. ||