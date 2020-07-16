# ButtonGlyph property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property ButtonGlyph: TPJAboutBtnGlyphs;

type TPJAboutBtnGlyphs = (
  abgOK, abgCancel, abgIgnore, abgClose, abgNone
);
```

## Description

The About box contains one button which is used to close the dialog box. The button can display a glyph (bitmap) to indicate its use. This property is used to determine which (if any) glyph to display. Valid values for the property and their meanings are as follows:

|   Value   |   Meaning   |
|-----------|-------------|
| _abgOK_ | A green check mark appears on the button face. |
| _abgCancel_ | A red cross appears on the button face. |
| _abgIgnore_ | A green man walking away appears on the button face. |
| _abgClose_ | A door appears on the button face. |
| _abgNone_ | No glyph is displayed on the button. |

_ButtonGlyph_ defaults to _abgNone_.
