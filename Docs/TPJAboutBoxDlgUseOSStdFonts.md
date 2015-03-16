<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# UseOSStdFonts property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property UseOSStdFonts: Boolean;
```

## Description ##

When true this property forces the dialog box to use the operating system's default font. When false the dialog's own font is used.

The property is designed to enable the default UI fonts of Windows XP and later to be used.

The default value is False.

Note that the [Font](TPJAboutBoxDlgFont.md) property is ignored when UseOSStdFonts is True.