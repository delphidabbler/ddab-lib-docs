# ButtonGroup property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJWinMsgDlg](TPJWinMsgDlg.md)_

```pascal
type
  TPJMsgDlgButtonGroup = (
    bgAbortRetryIgnore, bgOK, bgOKCancel, bgRetryCancel, bgYesNo, bgYesNoCancel,
    bgUnknown, bgCancelTryContinue
  );

property ButtonGroup: TPJMsgDlgButtonGroup;
```

## Description ##

The buttons which appear in the dialogue box depend on the value of this property. The possible values are:

| **Value** | **Buttons used** |
|:----------|:-----------------|
| `bgAbortRetryIgnore` | Abort, Retry and Ignore buttons. |
| `bgOK` | A single OK button. |
| `bgOKCancel` | An OK and a Cancel button. |
| `bgRetryCancel` | A Retry and a Cancel button. |
| `bgYesNo` | A Yes and a No button. |
| `bgYesNoCancel` | Yes, No and Cancel buttons. |
| `bgUnknown` | An unsupported or unknown group of buttons. This item is for use in _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_ and should not be selected in _TPJWinMsgDlg_. If it is selected it has the same effect as `bgOK`. |
| `bgCancelTryContinue` | Cancel, Try Again and Continue buttons. This button group requires the Windows NT platform and Windows 2000 or later. Behaves as `bgAbortRetryIgnore` when specified on OSs that do not support this button group. |

Setting _ButtonGroup_ also updates the _[DlgType](TPJWinMsgDlgDlgType.md)_ property and vice versa. See the _[DlgType page](TPJWinMsgDlgDlgType.md)_ for full details.

To include a help button in the dialogue box set the _[HelpContext](TPJWinMsgDlgHelpContext.md)_ property to some non-zero value.

A value associated with the button that was clicked is returned from the _[Execute](TPJWinMsgDlgExecute.md)_ method.

The default value of the property is `bgOK`.