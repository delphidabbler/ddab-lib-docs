# Example 4: Using string information properties

This example demostrates how to access string information from a version resource using _[TPJVersionInfo](../API/TPJVersionInfo.md)_. It demonstrates two methods - the first using dedicated properties such as _LegalCopyright_ and the second using the _[StringFileInfo](../API/TPJVersionInfo-StringFileInfo.md)_ property. The example also demonstrates the use of the _[FileName](../API/TPJVersionInfo-FileName.md)_ property to access information in other files.

Drop a _TMemo_, two _TButton_ controls and a _[TPJVersionInfo](../API/TPJVersionInfo.md)_ component onto a form and add the following function and event handlers:

```pascal
function DirToPath(const Dir: string): string;
  // Ensures path end in '\'
begin
  if (Dir <> '') and (Dir[Length(Dir)] <> #$5C) then
    Result := Dir + #$5C
  else
    Result := Dir;
end;

function WindowsDir: string;
  // Returns Windows directory
begin
  SetLength(Result, MAX_PATH);
  SetLength(Result, GetWindowsDirectory(PChar(Result), MAX_PATH));
end;

function SystemDir: string;
  // Returns Windows System directory
begin
  SetLength(Result, MAX_PATH);
  SetLength(Result, GetSystemDirectory(PChar(Result), MAX_PATH));
end;

function FindProg(const ExeName: string): string;
  // Finds program in Windows or System directory
begin
  Result := DirToPath(WindowsDir) + ExeName;
  if FileExists(Result) then Exit;

  Result := DirToPath(SystemDir) + ExeName;
  if not FileExists(Result) then
    raise Exception.CreateFmt(
      'Can''t find %s in Windows or System folders', [ExeName]
    );
end;

procedure TEgForm2.Button1Click(Sender: TObject);
begin
  // Get version info for Calc.exe
  PJVersionInfo1.FileName := FindProg('Calc.exe');
  with Memo1.Lines do
  begin
    // Clear the memo and write narrative
    Clear;
    Add('String information block for Windows'
      + ' Calculator (method 1)');
    Add('');
    // Add string information using dedicated properties
    Add('Comments: ' + PJVersionInfo1.Comments);
    Add('CompanyName: ' + PJVersionInfo1.CompanyName);
    Add('FileDescription: ' + PJVersionInfo1.FileDescription);
    Add('FileVersion: ' + PJVersionInfo1.FileVersion);
    Add('InternalName: ' + PJVersionInfo1.InternalName);
    Add('LegalCopyright: ' + PJVersionInfo1.LegalCopyright);
    Add('LegalTrademarks: ' + PJVersionInfo1.LegalTrademarks);
    Add('OriginalFileName: ' + PJVersionInfo1.OriginalFileName);
    Add('PrivateBuild: ' + PJVersionInfo1.PrivateBuild);
    Add('ProductName: ' + PJVersionInfo1.ProductName);
    Add('ProductVersion: ' + PJVersionInfo1.ProductVersion);
    Add('SpecialBuild: ' + PJVersionInfo1.SpecialBuild);
  end;
end;

procedure TEgForm2.Button2Click(Sender: TObject);

  procedure AddStrInfo(StrName: string);
    // Add string info to memo by name
  begin
    Memo1.Lines.Add(StrName + ': ' +
      PJVersionInfo1.StringFileInfo[StrName]);
  end;

begin
  // Get string info for Notepad.exe
  PJVersionInfo1.FileName := FindProg('Notepad.exe');
  // Clear memo and write narrative
  Memo1.Clear;
  Memo1.Lines.Add('String information block for Windows'
      + ' NotePad (method 2)');
  Memo1.Lines.Add('');
  // Add string info using string info names
  AddStrInfo('Comments');
  AddStrInfo('CompanyName');
  AddStrInfo('FileDescription');
  AddStrInfo('FileVersion');
  AddStrInfo('InternalName');
  AddStrInfo('LegalCopyright');
  AddStrInfo('LegalTrademarks');
  AddStrInfo('OriginalFileName');
  AddStrInfo('PrivateBuild');
  AddStrInfo('ProductName');
  AddStrInfo('ProductVersion');
  AddStrInfo('SpecialBuild');
end;

procedure TEgForm2.FormShow(Sender: TObject);
  // ensure the memo is clear
begin
  Memo1.Clear;
end;
```

When the first button is clicked the memo is populated with string information extracted from the Windows Calculator program while clicking the second button uses a different method to extract and displays string information about the NotePad program.

**Links:**

* Back to the [Examples List](../Examples.md)
* Back to the [Main Component Page](../../VerInfo.md)
