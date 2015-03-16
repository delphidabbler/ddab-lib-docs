<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# Position property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property Position: TPJAboutPosition;

type TPJAboutPosition = (abpScreen, abpDesktop, abpOwner);
```

## Description ##

The _Position_ property determines whether the _[CentreDlg](TPJAboutBoxDlgCentreDlg.md)_, _[DlgTop](TPJAboutBoxDlgDlgTop.md)_ and _[DlgLeft](TPJAboutBoxDlgDlgLeft.md)_ properties act relative  to screen, desktop or owning form. Valid values for the property and their meanings are as follows:

| **Value** | **Text** |
|:----------|:---------|
| `abpScreen` | The dialog is positioned relative to the screen. |
| `abpDesktop` | The dialog is positioned relative to the desktop's work area (this takes into account the taskbar and toolbars). |
| `abpOwner` | The dialog is positioned relative to its owner - usually the form on which the component is dropped. If the component has no owner, or the owner is not a window control, then this setting has no effect and positioning is per `abpScreen`. |

The default value is `abpDesktop`.