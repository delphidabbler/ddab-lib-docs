# DlgTop property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property DlgTop: Integer;
```

## Description

The _DlgTop_ property determines the position of the top of the about dialog box in pixels. Whether the top of the dialog is aligned relative to the screen, the desktop work area or the owning control depends on the value of the [_Position_](./TPJAboutBoxDlg-Position.md) property. The alignment may be adjusted to ensure the whole of the dialog can be seen.

If the [_CentreDlg_](./TPJAboutBoxDlg-CentreDlg.md) property is true then _DlgTop_ is ignored and the dialog is centred.

The default value is `0`.
