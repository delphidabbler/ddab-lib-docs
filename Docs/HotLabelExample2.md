# Examples: Using the OnCustomHint event. #

These examples show how to use the _[OnCustomHint](TPJHotLabelOnCustomHint.md)_ event of _[TPJHotLabel](TPJHotLabel.md)_. We handle the event to display a hint containing some descriptive text along with the URL in brackets.

## Example 1 ##

Drop a _[TPJHotLabel](TPJHotLabel.md)_ component on a form and create a _FormCreate_ and a _[OnCustomHint](TPJHotLabelOnCustomHint.md)_ event handler, completed as follows:

```pascal
procedure TForm1.FormCreate(Sender: TObject);
begin
  // You *could* set these properties at design time in the object inspector
  // instead of setting them here
  PJHotLabel1.URL := 'https://delphidabbler.com/';
  PJHotLabel1.HintStyle := hsCustom;
  PJHotLabel1.ShowHint := True;
end;

procedure TForm1.PJHotLabel1CustomHint(Sender: TObject; var HintStr: string);
begin
  HintStr := Format('View the site''s index page (%s)',  [PJHotLabel1.URL]);
end;
```

## Example 2 ##

This example is similar to the first except we store the custom hint text in the Hint property rather than entering the text in the form unit. This keeps the form's text in the form file. Drop a _[TPJHotLabel](TPJHotLabel.md)_ component on a form and create a _FormCreate_ and a _[OnCustomHint](TPJHotLabelOnCustomHint.md)_ event handler as before, and complete them as follows:

```pascal
procedure TForm1.FormCreate(Sender: TObject);
begin
  // You *could* set these properties at design time in the object inspector
  // instead of setting them here
  PJHotLabel1.Hint := 'View the site''s index page (%s)';
  PJHotLabel1.URL := 'https://delphidabbler.com/';
  PJHotLabel1.HintStyle := hsCustom;
  PJHotLabel1.ShowHint := True;
end;

procedure TForm1.PJHotLabel1CustomHint(Sender: TObject; var HintStr: string);
begin
  HintStr := Format(HintStr, [PJHotLabel1.URL]);
end;
```

**Link:**

  * Back to [Hot Label Component Page](HotLabelComponent.md)