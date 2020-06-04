# Message dialogue Components FAQ

This page has some frequently asked questions about the DelphiDabbler Message dialogue Components {TODO: add link}. You can also try the components' documentation {TODO: add link}.

----

**Can I change the colour of the dialogue box window?**

Yes and no!

With `TPJWinMsgDlg` (and the deprecated `TPJMessageDialog`) you can't do this because this component is just a wrapper around Windows API calls that do not permit the colour to be changed.

It is possible using `TPJVCLMsgDlg`, which wraps Delphi VCL calls which use a normal Delphi `TForm` to implement the dialogue box. The component's `OnShow` event gives access to the dialogue form. Just handle the event and change the form's colour in the event handler, like this:

```pascal
procedure TForm1.PJVCLMsgDlg1Show(Sender: TObject; Dlg: TForm);
var
  I: Integer;
begin
  Dlg.Color := clWindow; // replace this with your desired colour
end;
```

Note that the `Dlg` parameter is a reference to the dialogue box form while `Sender` is a reference to the component. `Dlg` is valid only while the dialogue is being displayed.

> You need v2.2 or later of the components for this to work.

----

**Can I change the colour of the dialogue box buttons?**

No. `TPJWinMsgDlg` (and the deprecated `TPJMessageDialog`) are simply wrappers round Windows API calls that do not expose this behaviour. `TPJVCLMsgDlg` uses standard Delphi `TButton` controls which do not allow their colour to be changed.

----

**How do I get access to the controls used in a dialogue box displayed by TPJVCLMsgDlg?**

Handle the component's `OnShow` event and enumerate the controls owned by the form referenced by the `Dlg` parameter. The following example displays the class and name of each control on the dialogue box form in a `TMemo` control.

```pascal
procedure TForm1.PJVCLMsgDlg1Show(Sender: TObject; Dlg: TForm);
var
  Ctl: TComponent;
  I: Integer;
begin
  Memo1.Clear;
  for I := 0 to Pred(Dlg.ComponentCount) do
  begin
    Ctl := Dlg.Components[I];
    Memo1.Lines.Add(Ctl.ClassName + ' : ' + Ctl.Name);
  end;
end;
```

> You need v2.2 or later of the components for this to work.
