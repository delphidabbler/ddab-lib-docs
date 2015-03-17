# OnHide event #

**Project:** [Message Dialogue Components](MessageDialogComponents.md).

**Unit:** _PJMessageDialog_.

**Class:** _[TPJVCLMsgDlg](TPJVCLMsgDlg.md)_

```pascal
type
  TPJVCLMsgDlgFormEvent = procedure(
    Sender: TObject; Dlg: TForm
  ) of object;

property OnHide: TPJVCLMsgDlgFormEvent;
```

## Description ##

The _OnHide_ event is triggered just after the component's dialogue box is hidden when it is closed. A reference to the component itself is passed to the event handler's _Sender_ parameter while the _Dlg_ parameter references the dialogue box form.

The _Dlg_ parameter can be used to tidy up any customisation performed in the _[OnShow](TPJVCLMsgDlgOnShow.md)_ event handler. Most customisations do not need to be tidied up, but the handler has uses on occasions where there may be results to be read from customisations or where any non-component objects created in _[OnShow](TPJVCLMsgDlgOnShow.md)_ need to be freed.

**Warning:** The form referenced by the _Dlg_ parameter is destroyed shortly after _OnHide_ returns, so should not be referenced after the handler has completed. The form reference is the same one that is provided to the _[OnShow](TPJVCLMsgDlgOnShow.md)_ event handler.