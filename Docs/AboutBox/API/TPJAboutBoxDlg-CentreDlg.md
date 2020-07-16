# CentreDlg property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property CentreDlg: Boolean;
```

## Description

This property determines whether the About dialog box appears centred or not.

When _CentreDlg_ is set to True then the dialog box is centred over the screen, the desktop work area or the owner control, according to the value of the [_Position_](./TPJAboutBoxDlg-Position.md) property. The [_DlgLeft_](./TPJAboutBoxDlg-DlgLeft.md) and [_DlgTop_](./TPJAboutBoxDlg-DlgTop.md) properties are ignored in this case. The position of the dialog box may be adjusted to ensure it can all be seen.

When _CentreDlg_ is set to False the [_DlgLeft_](./TPJAboutBoxDlg-DlgLeft.md) and [_DlgTop_](./TPJAboutBoxDlg-DlgTop.md) properties determine the position of the dialog box.

The default value is _True_.
