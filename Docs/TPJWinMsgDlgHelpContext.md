# HelpContext property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJWinMsgDlg](TPJWinMsgDlg.md)_

```pascal
type
  THelpContext = -MaxLongInt..MaxLongInt;

property HelpContext: THelpContext;
```

## Description ##

Set the _HelpContext_ property to the context number of the relevant topic in the help file specified by the _[HelpFile](TPJWinMsgDlgHelpFile.md)_ property. When a non-zero help context number is specified a help button is displayed in the dialogue box which calls context sensitive help with the given help context when pressed.

Changing the value of _HelpContext_ from zero to non-zero and back again changes the value of the _[DlgType](TPJWinMsgDlgDlgType.md)_ property. See the _[DlgType page](TPJWinMsgDlgDlgType.md)_ for full details.

If _[OnHelp](TPJWinMsgDlgOnHelp.md)_ is not handled and a help button is pressed, a request is made to the _Application_ object to pass the help context along to the currently registered help system.