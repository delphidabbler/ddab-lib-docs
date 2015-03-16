<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# DlgTop property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property DlgTop: Integer;
```

## Description ##

The _DlgTop_ property determines the position of the top of the about dialog box in pixels. Whether the top of the dialog is aligned relative to the screen, the desktop work area or the owning control depends on the value of the _[Position](TPJAboutBoxDlgPosition.md)_ property. The alignment may be adjusted to ensure the whole of the dialog can be seen.

If the _[CentreDlg](TPJAboutBoxDlgCentreDlg.md)_ property is true then _DlgTop_ is ignored and the dialog is centred.

The default value is 0.