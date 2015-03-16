<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# ButtonGlyph property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property ButtonGlyph: TPJAboutBtnGlyphs;

type TPJAboutBtnGlyphs = (
  abgOK, abgCancel, abgIgnore, abgClose, abgNone
);
```

## Description ##

The About box contains one button which is used to close the dialog box. The button can display a glyph (bitmap) to indicate its use. This property is used to determine which (if any) glyph to display. Valid values for the property and their meanings are as follows:


| **Value** | **Meaning** |
|:----------|:------------|
| `abgOK` | A green check mark appears on the button face. |
| `abgCancel` | A red cross appears on the button face. |
| `abgIgnore` | A green man walking away appears on the button face. |
| `abgClose` | A door appears on the button face. |
| `abgNone` | No glyph is displayed on the button. |

_ButtonGlyph_ defaults to `abgNone`. (Was `abgOK` in versions prior to v3.5).