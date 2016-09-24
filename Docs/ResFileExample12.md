# Example #12: Recording a compilation date in a resource file<sup>v1.1†</sup> #

_† **Note:** The first block of code in this example requires v1.1 of the Resource File Unit if compiled with Delphi 2009 or later. When compiled with an earlier compiler v1.0 will suffice._

Sometimes it's useful for a program to "know" the date when it was last compiled. One way to do this is to include a resource in the program that contains the compile date. The program can then read the date from the resource when it needs it.

The downside of this is that before each build the resource file containing the date has to be modified. There are going to be times when this will be forgotten and the compiled program will contain the wrong date.

Using the Resource File Unit unit can automate this process by creating a command line program that can be included in an automated build process.

To begin with, here's routine that will store the current date, as an ANSI string, in a given resource file. If the resource already contains a date resource then it is overwritten. If there is no such resource then one is created.

Here's the code:

```pascal
uses
  SysUtils, Classes, Windows, PJResFile;

procedure UpdateResFile(const ResFileName: string);
var
  ResFile: TPJResourceFile;
  DateResource: TPJResourceEntry;
  DateStr: string;
const
  DateResourceName = 'COMPILEDATE';
begin
  ResFile := TPJResourceFile.Create;
  try
    // 1: Load any existing file
    if FileExists(ResFileName) then
      ResFile.LoadFromFile(ResFileName);
    // 2: Check if there's already a suitable resource
    DateResource := ResFile.FindEntry(RT_RCDATA, DateResourceName);
    if not Assigned(DateResource) then
      // no such resource: create one
      DateResource := ResFile.AddEntry(RT_RCDATA, DateResourceName);
    // 3: Store the current date in the resource
    DateStr := FormatDateTime('yyyy"-"mm"-"dd hh":"mm":"ss', Now);
    {$IFDEF UNICODE}
    DateResource.DataBytes := TEncoding.Default.GetBytes(DateStr);
    {$ELSE}
    DateResource.Data.Size := 0;  // clear any existing date
    DateResource.Data.WriteBuffer(Pointer(DateStr)^, Length(DateStr));
    DateResource.Data.Position := 0;
    {$ENDIF}
    // 4: Save the modified resource file
    ResFile.SaveToFile(ResFileName);
  finally
    ResFile.Free;
  end;
end;
```

Here's how it works:

  1. _Load any existing file:_ Check if the resource file already exists and if so we load it.
  1. _Check if there's already a suitable resource:_ Check if the required resource already exists and if so we keep a reference to it so the data can be overwritten. If the required resource doesn't exist we create it.
  1. _Store the current date in the resource:_ The current date is formatted and stored in _DateStr_. The next step depends on if a Unicode version of Delphi is being used or not. If so we simply convert _DateStr_ to its ANSI representation in a byte array and assign that to the _[DataBytes](TPJResourceEntry.md#properties)_**<sup>v1.1</sup>** property, which overwrites any existing value. If a Unicode compiler is not being used we use _[Data](TPJResourceEntry.md#properties)_ property instead, first clearing the stream, then write copying the (ANSI) string to it before reseting the stream pointer.
  1. _Save the modified resource file:_ Any existing file is overwritten.

Note that any existing resources in the file are preserved. If the resource file contained the "data" resource it is overwritten, but if the file had no such resource one is added. If the resource file didn't exist a new file is created with a single "date" resource.

Any program using the resource has to simply read the date string as ANSI text, convert it to a _TDateTime_ etc. if necessary and use it as required.

Of course you could always store a raw _TDateTime_ value in resources instead of a format string. To do this replace the declaration of _DateStr_ with a new local variable _DateNow_ with type _TDateTime_ and replace the code in the section introduced by the `// 3: Store the current date in the resource` comment with the following:

```pascal
    ...
    // 3: Store the current date in the resource
    DateNow := Now;
    DateResource.Data.Size := 0;
    DateResource.Data.WriteBuffer(DateNow, SizeOf(DateNow));
    DateResource.Data.Position := 0;
    // 4: Save the modified resource file
    ...
```

This routine could be included in a console application that takes the resource file name as a parameter then updates or creates the resource file containing the current date, like this:

```pascal
program DateIns;

{$APPTYPE CONSOLE}

uses
  SysUtils,
  Classes,
  Windows,
  PJResFile in 'PJResFile.pas';

{$R *.res}

// Insert UpdateResFile procedure here

var
  ResFileName: string;
begin
  try
    ResFileName := ParamStr(1);
    if ResFileName = '' then
      raise Exception.Create(
        'Resource file name must be passed on the command line'
      );
    UpdateResFile(ResFileName);
    ExitCode := 0;
  except
    on E: Exception do
    begin
      WriteLn('Error: ', E.Message);
      ExitCode := 1;
    end;
  end;
end.
```

You can then insert this program in your build tool chain.

**Links:**

  * [Previous Example](ResFileExample11.md)
  * Back to [List of Examples](ResFileExamples.md)
