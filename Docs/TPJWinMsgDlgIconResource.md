# IconResource property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJWinMsgDlg](TPJWinMsgDlg.md)_

```pascal
property IconResource: string;
```

## Description ##

Set _IconResource_ to identify the resource to be used to display a user defined icon in the dialogue box. If _IconResource_ is left blank then the default resource name "MAINICON" is used. The icon resource must be contained in the executable file. If such a resource cannot be found then no icon is displayed.

The _[Kind](TPJWinMsgDlgKind.md)_ property must be set to `mkUser` in order to display a user defined icon, otherwise _IconResource_ is ignored.

**Note 1:** "MAINICON" is the resource name of the application's main icon in Delphi.

**Note 2:** To reference an icon resource with a numeric id (rather than a string name) preceed the numeric value by a '#' character.