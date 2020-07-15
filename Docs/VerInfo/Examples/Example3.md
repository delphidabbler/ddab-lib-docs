# Example 3: Using translation, character set and language properties

This example shows how to use the translation, character set and language properties of _[TPJVersionInfo](../API/TPJVersionInfo.md)_ to display details of the language and character set for all translations in a file's version info. The example assumes the application contains version information. If this is not the case then a message to that effect is displayed in the list box.

Drop a _TListBox_ and a _[TPJVersionInfo](../API/TPJVersionInfo.md)_ component on a form and add the following _OnCreate_ event handler to the form:

```pascal
procedure TEgForm1.FormCreate(Sender: TObject);
var
  I: Integer;
begin
  ListBox1.Clear;
  // loop thru all translations
  if PJVersionInfo1.HaveInfo then
    for I := 0 to Pred(PJVersionInfo1.NumTranslations) do
    begin
      // make the current translation current
      PJVersionInfo1.CurrentTranslation := I;
      // add language and char set info to the list box

      ListBox1.Items.Add(
        Format(
          'Language: %s (%0.4X) -- CharSet: %s (%0.4X)',
          [PJVersionInfo1.Language, PJVersionInfo1.LanguageCode,
          PJVersionInfo1.CharSet, PJVersionInfo1.CharSetCode]
        )
      );
    end
  else
    ListBox1.Items.Add('NO VERSION INFO');
end;
```

When the form is displayed details of languages and character sets for each translation are displayed in the list box.

**Links:**

* Back to the [Examples List](../Examples.md)
* Back to the [Main Component Page](../../VerInfo.md)
