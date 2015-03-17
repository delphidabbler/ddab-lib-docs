# TPJWinMsgDlg #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

_TPJWinMsgDlg_ provides a customisable Windows message dialogue box. The component wraps the Windows _MessageBoxIndirect_ API call.

Its properties are a subset of those of _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_. _TPJWinMsgDlg_ is recommended for new projects requiring a Windows message box. If even greater control over the appearance of the dialogue is required then use _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_.

The text displayed in the dialogue box is determined by the _[Text](TPJWinMsgDlgText.md)_ property. Various button groupings can be displayed using the _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ property. Setting a non-zero _[HelpContext](TPJWinMsgDlgHelpContext.md)_ causes a help button to be displayed. The _[Kind](TPJWinMsgDlgKind.md)_ property allows a choice of various standard windows icons to be displayed. A user defined icon extracted from a named resource, specified by _[IconResource](TPJWinMsgDlgIconResource.md)_ can also be displayed. The window title can be set using the _[Title](TPJWinMsgDlgTitle.md)_ property, otherwise a default title, related to the kind of icon being displayed is used. The _[MakeSound](TPJWinMsgDlgMakeSound.md)_ property determines whether an appropriate system sound is generated when the dialogue is displayed.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[Execute](TPJWinMsgDlgExecute.md)_ | Displays the dialogue box and returns information about the button pressed to close it. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[ButtonGroup](TPJWinMsgDlgButtonGroup.md)_ | Determines which buttons appear in the dialogue box. |
| _[DlgType](TPJWinMsgDlgDlgType.md)_ | Permits the buttons and type of dialogue box displayed to be specified by means of the flags that are passed to the _uType_ parameter of the Windows _MessageBox_ API function. |
| _[HelpContext](TPJWinMsgDlgHelpContext.md)_ | Specifies the context number for online help and displays a help button. |
| _[HelpFile](TPJWinMsgDlgHelpFile.md)_ | Specifies the file to use for online help. |
| _[IconResource](TPJWinMsgDlgIconResource.md)_ | Specifies the resource containing the dialogue box's icon. |
| _[Kind](TPJWinMsgDlgKind.md)_ | Determines the type of dialogue box that is displayed. |
| _[MakeSound](TPJWinMsgDlgMakeSound.md)_ | Flag that determines if a sound will be emitted when the dialogue box is displayed. |
| _[Text](TPJWinMsgDlgText.md)_ | The text that is displayed in the dialogue box. |
| _[Title](TPJWinMsgDlgTitle.md)_ | The dialogue box's window title. |

## Events ##

| **Event** | **Description** |
|:----------|:----------------|
| _[OnHelp](TPJWinMsgDlgOnHelp.md)_ | Event triggered when a user requests help in a dialogue box. |