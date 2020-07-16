# Notes property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property Notes: string;
```

## Description

The _Notes_ property is used to store the notes to be displayed in the about box. The notes appear at the bottom of the text area. The text will word-wrap up to three lines. When setting the property at run time end of line characters can be included in the string to force line breaks.

The default value for this property is an empty string, which displays nothing.

**Note**: If the [_VersionInfo_](./TPJAboutBoxDlg-VersionInfo.md) property is not nil then _Notes_ is ignored.
