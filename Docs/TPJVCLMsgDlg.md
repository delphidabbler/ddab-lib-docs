# TPJVCLMsgDlg #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

_TPJVCLMsgDlg_ provides a customisable message dialogue box that is based on that provided by the Delphi _CreateMessageDialog_ function. The component provides a similar (but extended) interface to the _[TPJWinMsgDlg](TPJWinMsgDlg.md)_ component but uses a different method to display the dialogue box. This component is recommended when a finer degree of control to that provided by _[TPJWinMsgDlg](TPJWinMsgDlg.md)_ is required.

The text displayed in the dialogue box is determined by the _[Text](TPJVCLMsgDlgText.md)_ property. Various button groupings can be displayed using the _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ and/or _[Buttons](TPJVCLMsgDlgButtons.md)_ properties. Setting a non-zero _[HelpContext](TPJVCLMsgDlgHelpContext.md)_ causes a help button to be displayed. The _[Kind](TPJVCLMsgDlgKind.md)_ property allows a choice of various standard dialogue boxes and icons to be displayed. A user defined icon extracted from a named resource, specified by _[IconResource](TPJVCLMsgDlgIconResource.md)_ can also be displayed. The window title can be customised using the _[Title](TPJVCLMsgDlgTitle.md)_ property, otherwise a default title is used that is related to the kind of icon being displayed. The _[MakeSound](TPJVCLMsgDlgMakeSound.md)_ property determines whether an appropriate system sound is generated when the dialogue is displayed. It is possible to set how the dialogue box is to be aligned to screen or form using the _[Align](TPJVCLMsgDlgAlign.md)_ property in combination with the _[OffsetLeft](TPJVCLMsgDlgOffsetLeft.md)_ and _[OffsetTop](TPJVCLMsgDlgOffsetTop.md)_ properties.

The dialogue box can be invoked with the _[Execute](TPJVCLMsgDlgExecute.md)_ method or an instance of the dialogue can be created using the _[CreateDialog](TPJVCLMsgDlgCreateDialog.md)_ method. In the latter case the user has responsibility for showing and hiding the dialogue and destroying the instance.

## Methods ##

| **Method** | **Description** |
|:-----------|:----------------|
| _[CreateDialog](TPJVCLMsgDlgCreateDialog.md)_ | Creates instance of  the dialogue box and returns a reference to it. |
| _[Execute](TPJVCLMsgDlgExecute.md)_ | Displays the dialogue box and returns information about the button pressed to close it. |

## Properties ##

| **Property** | **Description** |
|:-------------|:----------------|
| _[Align](TPJVCLMsgDlgAlign.md)_ | Determines the on screen alignment of the dialogue box. |
| _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ | Determines which buttons appear in the dialogue box. |
| _[Buttons](TPJVCLMsgDlgButtons.md)_ | Determines the buttons displayed in the dialogue box . Provides finer control than _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_. |
| _[DefButton](TPJVCLMsgDlgDefButton.md)_ | Determines the default button in the dialogue box. |
| _[DlgType](TPJVCLMsgDlgDlgType.md)_ | Permits the buttons and type of dialogue box displayed to be specified by means of the flags that are passed to the _uType_ parameter of the Windows _MessageBox_ API function. |
| _[HelpContext](TPJVCLMsgDlgHelpContext.md)_ | Specifies the context number for online help. |
| _[HelpFile](TPJVCLMsgDlgHelpFile.md)_ | Specifies the file to use for online help. |
| _[IconResource](TPJVCLMsgDlgIconResource.md)_ | Specifies the resource containing the dialogue box's icon. |
| _[Kind](TPJVCLMsgDlgKind.md)_ | Determines the type of  dialogue box that is displayed. |
| _[MakeSound](TPJVCLMsgDlgMakeSound.md)_ | Flag that determines if a sound will be emitted when the dialogue box is displayed. |
| _[OffsetLeft](TPJVCLMsgDlgOffsetLeft.md)_ | Determines the offset of the dialogue box from the left of the screen or owning form. |
| _[OffsetTop](TPJVCLMsgDlgOffsetTop.md)_ | Determines the offset of the dialogue box from the top of the screen or owning form. |
| _[Options](TPJVCLMsgDlgOptions.md)_ | Property that records various customisation options. |
| _[Text](TPJVCLMsgDlgText.md)_ | The text that is displayed in the dialogue box. |
| _[Title](TPJVCLMsgDlgTitle.md)_ | The dialogue box's window title. |

## Events ##

| **Event** | **Description** |
|:----------|:----------------|
| _[OnHelp](TPJVCLMsgDlgOnHelp.md)_ | Event triggered when a user requests help in a dialogue box. |
| _[OnHide](TPJVCLMsgDlgOnHide.md)_ | Event triggered just after the component's dialogue box is hidden. |
| _[OnShow](TPJVCLMsgDlgOnShow.md)_ | Event triggered just before the component's dialogue box is displayed. |