# HelpFile property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJWinMsgDlg](TPJWinMsgDlg.md)_

```pascal
property HelpFile: string;
```

## Description ##

Set the _HelpFile_ property to specify the help file to be used when a Help button is clicked or F1 is pressed in the dialogue. If _HelpFile_ is set to the empty string then the help file associated with the parent form or application is used.

The _[HelpContext](TPJWinMsgDlgHelpContext.md)_ property is used to specify the help topic within the help file that is to be displayed.

If _[OnHelp](TPJWinMsgDlgOnHelp.md)_ is not handled and a help button is pressed, a request is made to the _Application_ object to pass the value of this property and the _[HelpContext](TPJWinMsgDlgHelpContext.md)_ property along to the currently registered help system.