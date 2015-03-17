# Title property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
type
  TCaption = type string;

property Title: TCaption;
```

## Description ##

Set this property to customise the string that is displayed as the dialogue box window title. Leaving this property empty causes a default title to be displayed that depends on the value of the _[Kind](TPJVCLMsgDlgKind.md)_ property.