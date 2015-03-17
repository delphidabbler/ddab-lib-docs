# MakeSound property #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
property MakeSound: Boolean;
```

## Description ##

Set _MakeSound_ to `True` to play a sound when the dialogue is displayed. If _MakeSound_ is `False` then no sound is played.

The sound played is one of the standard system sounds. Which sound is used depends on the value of the _[Kind](TPJVCLMsgDlgKind.md)_ property, the operating system version and the chosen sound theme. Some themes will play no sound for some values of the _[Kind](TPJVCLMsgDlgKind.md)_ property regardless of the value assigned to _MakeSound_.

The property's default value is `False`.