# ButtonGroup property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
type
  TPJMsgDlgButtonGroup = (
    bgAbortRetryIgnore, bgOK, bgOKCancel, bgRetryCancel, bgYesNo, bgYesNoCancel,
    bgUnknown, bgCancelTryContinue
  );

property ButtonGroup: TPJMsgDlgButtonGroup;
```

## Description ##

The buttons which appear in the dialogue box depend on the value of this property and on the associated _[Buttons](TPJVCLMsgDlgButtons.md)_ property.

When the value of _ButtonGroup_ is changed the _[Buttons](TPJVCLMsgDlgButtons.md)_ property is updated the to the set of buttons contained in the button group. Setting _ButtonGroup_ to `bgUnkown` sets _[Buttons](TPJVCLMsgDlgButtons.md)_ to the empty set. Conversely, when the _[Buttons](TPJVCLMsgDlgButtons.md)_ property is changed _ButtonGroup_ is set to any matching group, or to `bgUnknown` if the set of buttons in the _[Buttons](TPJVCLMsgDlgButtons.md)_ property is not a valid button group.

**Note:** Normally, setting _ButtonGroup_ to a value other than `bgUnkown` and then adding `mbHelp` to the resulting _[Buttons](TPJVCLMsgDlgButtons.md)_ set causes _ButtonGroup_ to change to `bgUnknown`. To prevent this include `mdoGroupIgnoresHelp` in the _[Options](TPJVCLMsgDlgOptions.md)_ property. Setting this option means that `mbHelp` is ignored when trying to match _[Buttons](TPJVCLMsgDlgButtons.md)_ to a valid button group and, in the case above, _ButtonGroup_ will remain unchanged when `mbHelp` is added to _[Buttons](TPJVCLMsgDlgButtons.md)_.

Setting _ButtonGroup_ also updates the _[DlgType](TPJVCLMsgDlgDlgType.md)_ property and vice versa. See the _[DlgType page](TPJVCLMsgDlgDlgType.md)_ for full details.

The possible values of _ButtonGroup_ are as follows:

| **Value** | **Buttons used** |
|:----------|:-----------------|
| `bgAbortRetryIgnore` | Abort, Retry and Ignore buttons. |
| `bgOK` | A single OK button. |
| `bgOKCancel` | An OK and a Cancel button. |
| `bgRetryCancel` | A Retry and a Cancel button. |
| `bgYesNo` | A Yes and a No button. |
| `bgYesNoCancel` | Yes, No and Cancel buttons. |
| `bgUnknown` | An unsupported or unknown group of buttons. This item should not be selected explicitly. If it is selected it has the same effect as `bgOK`. |
| `bgCancelTryContinue` | Synonym for `bgAbortRetryIgnore` with same effect. (Note that in _[TPJWinMsgDlg](TPJWinMsgDlg.md)_ `bgCancelTryContinue` behaves differently to `bgAbortRetryIgnore`.) |

To include a help button in the dialogue box do one of two things:

  1. Set the _[HelpContext](TPJVCLMsgDlgHelpContext.md)_ property to some non-zero value and include `mdoAutoHelpBtn` in the _[Options](TPJVCLMsgDlgOptions.md)_ property, or
  1. Include the `mbHelp` button value in the _[Buttons](TPJVCLMsgDlgButtons.md)_ property.

If a cancel button is included in the group whether it appears or not depends on whether the `mdoInhibitCancel` value is included in the _[Options](TPJVCLMsgDlgOptions.md)_ property.

A value associated with the button that was clicked is returned from the _[Execute](TPJVCLMsgDlgExecute.md)_ method.

The default value of the property is `bgOK`.