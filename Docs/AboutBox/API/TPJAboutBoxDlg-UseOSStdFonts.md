# UseOSStdFonts property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property UseOSStdFonts: Boolean;
```

## Description

When true this property forces the dialog box to use the operating system's default font. When false the dialog's own font is used.

The property is designed to enable the default UI fonts of Windows XP and later to be used.

The default value is _False_.

**Note** that the [_Font_](./TPJAboutBoxDlg-Font.md) property is ignored when _UseOSStdFonts_ is _True_.
