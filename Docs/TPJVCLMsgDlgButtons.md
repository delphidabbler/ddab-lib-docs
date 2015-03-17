# Buttons property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
type
  TMsgDlgButton = (
    mbYes, mbNo, mbOK, mbCancel, mbAbort, mbRetry, mbIgnore,
    mbAll, mbNoToAll, mbYesToAll, mbHelp, mbClose
  );

type TMsgDlgButtons = set of TMsgDlgBtn;

property Buttons: TMsgDlgButtons;
```

## Description ##

The _Buttons_ property records the set of buttons that are to appear in the dialogue box. This property is more flexible that the related _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ property - it supports additional buttons in any combination.

Setting the _Buttons_ property causes _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ to be updated. If the combination of buttons required is not supported by the _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ property, that property is set to `bgUnknown`. Conversely setting the _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ property causes the _Buttons_ property to be updated to the set of buttons in the selected group.

**Note:** Normally, setting _Buttons_ to a set of buttons supported by _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ and then including `mbHelp` in _Buttons_ will cause _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ to revert to `bgUnknown`. To prevent this include `mdoGroupIgnoresHelp` in the _[Options](TPJVCLMsgDlgOptions.md)_ property. When this option is included `mbHelp` is ignored when trying to match _Buttons_ to a valid button group.

Because of the link between _Buttons_ and _[ButtonGroup](TPJVCLMsgDlgButtonGroup.md)_ and its linkage with _[DlgType](TPJVCLMsgDlgDlgType.md)_, setting _Buttons_ can affect the value of _[DlgType](TPJVCLMsgDlgDlgType.md)_ and vice versa.

The set of available buttons (_TMsgDlgButtons_) is defined in the _Dialogs_ unit and is as follows:

| **Value** | **Button caption** | **ModalResult** |
|:----------|:-------------------|:----------------|
| `mbYes` | "Yes" | `mrYes` |
| `mbNo` | "No" | `mrNo` |
| `mbOK` | "OK" | `mrOK` |
| `mbCancel` | "Cancel" | `mrCancel` |
| `mbAbort` | "Abort" | `mrAbort` |
| `mbRetry` | "Retry" | `mrRetry` |
| `mbIgnore` | "Ignore" | `mrIgnore` |
| `mbAll` | "All" | `mrAll` |
| `mbNoToAll` | "No To All" | `mrNoToAll` |
| `mbYesToAll` | "Yes To All" | `mrYesToAll` |
| `mbHelp` | "Help" | N/a (doesn't close dialogue) |
| `mbClose` | "Close" | `mrClose` |

Note that if the _[Options](TPJVCLMsgDlgOptions.md)_ property includes `mdoAutoHelpBtn` then the display of a help button depends only on the value of the _[HelpContext](TPJVCLMsgDlgHelpContext.md)_ property - inclusion of `mbHelp` in the _Buttons_ property is ignored.

Similarly if `mdoInhibitCancel` is included in _[Options](TPJVCLMsgDlgOptions.md)_ a cancel button will never be displayed, regardless of whether `mbCancel` is included in _Buttons_.

Which button in the _Buttons_ set is to be the default button is specified by the _[DefButton](TPJVCLMsgDlgDefButton.md)_ property.

Note that if no buttons are specified for display, or if all the buttons specified in the _Buttons_ property are inhibited by _[Options](TPJVCLMsgDlgOptions.md)_ settings, then the dialogue will display an OK button. The Help button is ignored when determining the above since it does not close the dialogue, i.e. if only the Help button would be displayed then an OK button is also included.

The default value of the property is `[mbOK]`.