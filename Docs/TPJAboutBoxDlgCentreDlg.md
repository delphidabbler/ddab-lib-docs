<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# CentreDlg property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property CentreDlg: Boolean;
```

## Description ##

This property determines whether the About dialog box appears centred or not.

When _CentreDlg_ is set to True then the dialog box is centred over the screen, the desktop work area or the owner control, according to the value of the _[Position](TPJAboutBoxDlgPosition.md)_ property. The _[DlgLeft](TPJAboutBoxDlgDlgLeft.md)_ and _[DlgTop](TPJAboutBoxDlgDlgTop.md)_ properties are ignored in this case. The position of the dialog box may be adjusted to ensure it can all be seen.

When _CentreDlg_ is set to False the _DlgLeft_ and _DlgTop_ properties determine the position of the dialog box.

The default value is True.