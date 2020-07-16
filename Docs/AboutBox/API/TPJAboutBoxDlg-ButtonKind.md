# ButtonKind property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property ButtonKind: TPJAboutBtnKinds;

type TPJAboutBtnKinds = (
  abkOK, abkDone, abkClose, abkCancel
);
```

## Description

The About box contains one button which is used to close the dialog box. The button can display different text to indicate its use. The _ButtonKind_ property is used to determine which text to display. Valid values for the property and their meanings are as follows:

|   Value   |   Text   |
|-----------|----------|
| _abkOK_ | `OK` |
| _abkDone_ | `Done` |
| _abkClose_ | `Close` |
| _abkCancel_ | `Cancel` |

The default value is _abkOK_.

The button captions are stored as string resources and can be translated.
