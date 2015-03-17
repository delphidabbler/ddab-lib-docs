# OffsetLeft property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
property OffsetLeft: Integer;
```

## Description ##

The effect of _OffsetLeft_ is determined by the value of the _[Align](TPJVCLMsgDlgAlign.md)_ property as follows:

| **_Align_ property value** | **Effect of _OffsetLeft_** |
|:---------------------------|:---------------------------|
| `mdaScreenOffset` | Sets horizontal offset of dialogue box from left hand side of screen. |
| `mdaScreenCentre` | No effect: property is ignored. |
| `mdaFormOffset` | Sets horizontal offset of dialogue box from left hand side of owning form. |
| `mdaFormCentre` | No effect: property is ignored.|

_OffsetLeft_ is used in conjunction with _[OffsetTop](TPJVCLMsgDlgOffsetTop.md)_.

The default value of the property is 0.