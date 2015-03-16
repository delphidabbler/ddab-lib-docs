<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# ButtonKind property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property ButtonKind: TPJAboutBtnKinds;

type TPJAboutBtnKinds = (
  abkOK, abkDone, abkClose, abkCancel
);
```

## Description ##

The About box contains one button which is used to close the dialog box. The button can display different text to indicate its use. The _ButtonKind_ property is used to determine which text to display. Valid values for the property and their meanings are as follows:

| **Value** | **Text** |
|:----------|:---------|
| `abkOK` | 'OK' |
| `abkDone` | 'Done' |
| `abkClose` | 'Close' |
| `abkCancel` | 'Cancel' |

The default value is `abkOK`.

The button captions are stored as string resources and can be translated.