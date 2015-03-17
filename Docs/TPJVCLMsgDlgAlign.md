# Align property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
type
  TPJMsgDlgAlign = (
    mdaScreenCentre, mdaScreenOffset, mdaFormCentre, mdaFormOffset
  );

property Align: TPJMsgDlgAlign;
```

## Description ##

The _Align_ property determines the alignment of the dialogue box relative to either the screen or the owner form. The various values it can take are described below:

| **Value** | **Description** |
|:----------|:----------------|
| `mdaScreenCentre` | The dialogue is centred over the screen. |
| `mdaScreenOffset` | The dialogue is offset from the top left corner of the screen by the amount given by the values of the _[OffsetLeft](TPJVCLMsgDlgOffsetLeft.md)_ and _[OffsetTop](TPJVCLMsgDlgOffsetTop.md)_ properties. |
| `mdaFormCentre` | The dialogue is centred over the owning form. If no owning form can be found the dialogue is centred on the screen. |
| `mdaFormOffset` | The dialogue is offset relative to the top left corner of the owning form by the amount given by the values of the _[OffsetLeft](TPJVCLMsgDlgOffsetLeft.md)_ and _[OffsetTop](TPJVCLMsgDlgOffsetTop.md)_ properties. If no owing form can be found the dialogue is offset relative to the screen. |

The default value of the property is `mdaScreenCentre`.