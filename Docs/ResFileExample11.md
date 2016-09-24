# Example #11: Validating a resource file<sup>v1.1</sup> #

_**Note:** The code in this example requires v1.1 of the Resource File Unit and Delphi 2009 or later._

Suppose you have a resource file that is included in a program that you are compiling. There may be resources that your program assumes will be present and will crash if they are not there. Most likely there will also be resources that Windows expects to find, such as the program icon.

It could be useful if you could check for the presence of these resources before compiling your program.

Some of the most common resources are

  1. A main program icon named `MAINICON`.
  1. A manifest file.
  1. One or more bitmaps.

Here's a little routine that checks to see if a given resource file contains all of the above resource types. It also checks for the required bitmap resource names and that the manifest has the correct XML format. The routine raises exceptions if any errors are found. It returns normally only if the resource file is valid.

```pascal
uses
  SysUtils, StrUtils, Classes, Windows, PJResFile;

procedure ValidateResFile(const FileName: string;
  const BmpNames: array of string);
var
  ResFile: TPJResourceFile;
  Entry: TPJResourceEntry;
  Manifest: string;
  BmpName: string;
const
  ManifestID = '<assembly xmlns="urn:schemas-microsoft-com:asm.v1" '
    + 'manifestVersion="1.0">';
begin
  ResFile := TPJResourceFile.Create;
  try
    ResFile.LoadFromFile(FileName);
    // Check for main icon
    if not ResFile.EntryExists(RT_GROUP_ICON, 'MAINICON') then
      raise Exception.Create('MAINICON missing');
    // Check manifest exists and is valid
    Entry := ResFile.FindEntry(RT_MANIFEST, nil); // always only 1 manifest
    if not Assigned(Entry) then
      raise Exception.Create('Manifest missing');
    Manifest := TEncoding.UTF8.GetString(Entry.DataBytes);
    if not ContainsText(Manifest, ManifestID) then
      raise Exception.Create('Invalid manifest');
    // Check for required bitmaps
    for BmpName in BmpNames do
      if not ResFile.EntryExists(RT_BITMAP, PChar(BmpName)) then
        raise Exception.CreateFmt('Bitmap "%s" not found', [BmpName]);
  finally
    ResFile.Free;
  end;
end;
```

First we load the resource file whose name is supplied as a parameter. Next we check if the main icon resource exists. We then check that a manifest file exists. If so we load its contents (which are assumed to be UTF-8 encoded) and check for the existence of the correct XML tag. Finally we loop through the given array of bitmap resource names and check that each one is present.

This routine could be used in a command line application that could be incorporated in a build chain, for example:

```pascal
program ResourceFileChecker;

{$APPTYPE CONSOLE}

uses
  SysUtils,
  StrUtils,
  Classes,
  Windows,
  PJResFile in 'PJResFile.pas';

// *** Insert ValidateResFile procedure here ***

var
  FileName: string;
begin
  try
    FileName := ParamStr(1);
    if FileName = '' then
      raise Exception.Create(
        'Resource file name must be passed on command line'
      );
    ValidateResFile(
      FileName,
      ['TVCHECKBOXES', 'TEXTSEARCH', 'SELECTIONSEARCH',
      'XREFSEARCH', 'MODIFIED']
    );
    WriteLn('Resource file is valid');
    ExitCode := 0;  // success
  except
    on E: Exception do
    begin
      Writeln('Error: ', E.Message);
      ExitCode := 1;  // failure
    end;
  end;
end.
```

This program accepts the name of the resource file to be checked on the command line. First it validates the command line.

Then it calls _ValidateResFile_ passing the resource file name and an array of required bitmap resource names. If the procedure returns normally a message indicating success is written out and a zero exit code is returned to the operating system. If _ValidateResFile_ raises an exception the error message is written out and an exit code of 1 is returned.

**Links:**

  * [Next Example](ResFileExample12.md)
  * [Previous Example](ResFileExample10.md)
  * Back to [List of Examples](ResFileExamples.md)
