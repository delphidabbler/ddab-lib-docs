# Position property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property Position: TPJAboutPosition;

type TPJAboutPosition = (abpScreen, abpDesktop, abpOwner);
```

## Description

The _Position_ property determines whether the [_CentreDlg_](./TPJAboutBoxDlg-CentreDlg.md), [_DlgTop_](./TPJAboutBoxDlg-DlgTop.md) and [_DlgLeft_](./TPJAboutBoxDlg-DlgLeft.md) properties act relative  to screen, desktop or owning form. Valid values for the property and their meanings are as follows:

|   Value   |   Text   |
|-----------|----------|
| _abpScreen_ | The dialog is positioned relative to the screen. |
| _abpDesktop_ | The dialog is positioned relative to the desktop's work area (this takes into account the taskbar and toolbars). |
| _abpOwner_ | The dialog is positioned relative to its owner - usually the form on which the component is dropped. If the component has no owner, or the owner is not a window control, then this setting has no effect and positioning is per _abpScreen_. |

The default value is _abpDesktop_.
