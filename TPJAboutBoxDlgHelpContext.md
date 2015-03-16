<a href='Hidden comment: 
$Rev$
$Date$
'></a>

# HelpContext property #

**Project:** [About Box Component](AboutBoxComponent.md).

**Unit:** _PJAbout_.

**Class:** _[TPJAboutBoxDlg](TPJAboutBoxDlg.md)_

```
property HelpContext: THelpContext;

type THelpContext = -MaxLongInt..MaxLongInt;
```

## Description ##

_HelpContext_ stores the number of the help topic in the application's help file that is displayed when the F1 key is pressed. If _HelpContext_ is 0 then no help topic is displayed.

The default value is 0.