# HelpContext property

**Project:** [About Box Component](../API.md)

**Unit:** _PJAbout_.

**Class:** [_TPJAboutBoxDlg_](./TPJAboutBoxDlg.md)

```pascal
property HelpContext: THelpContext;

type THelpContext = -MaxLongInt..MaxLongInt;
```

## Description

_HelpContext_ stores the number of the help topic in the application's help file that is displayed when the F1 key is pressed. If _HelpContext_ is `0` then no help topic is displayed.

The default value is `0`.
