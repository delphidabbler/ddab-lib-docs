# OnShow event #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
type
  TPJVCLMsgDlgFormEvent = procedure(
    Sender: TObject; Dlg: TForm
  ) of object;

property OnShow: TPJVCLMsgDlgFormEvent;
```

## Description ##

The _OnShow_ event is triggered just before the component's dialogue box is displayed. A reference the component itself is passed to the event handler's _Sender_ parameter while the _Dlg_ parameter references the dialogue box form.

The _Dlg_ parameter can be used to customise the appearance of the dialogue box. Any tidying up of such customisation or any interpretation of the results of the customisation can be carried out by handling the _[OnHide](TPJVCLMsgDlgOnHide.md)_ event.

**Warning:** The form referenced by the _Dlg_ parameter is only valid while the dialogue box is displayed - it is destroyed when the dialogue is closed. It is safe to use the form reference during the _OnShow_ event handler and up until the _[OnHide](TPJVCLMsgDlgOnHide.md)_ event handler returns.