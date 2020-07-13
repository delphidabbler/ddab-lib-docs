# [Console Application Runner Classes](../../ConsoleApp.md)  Appendix 2: Console application source code

This appendix provides Delphi Pascal source code for two console applications that can be used with the various Console Application Runner Classes examples.

The source code is designed to work with Delphi 7 and later compilers. It works with both Unicode and non-Unicode versions of the compiler. The code _may_ compile with earlier compilers but this has not been tried.

## Timed

Usage:

```pascal
Timed [<seconds>]
```

Where `<seconds>` is a valid positive whole number.

This program runs for the number of seconds passed on the command line, or for 5 seconds if no such parameter is provided. It is useful for examples that require an application that runs for a reasonable or specified amount of time. The program outputs a sign-on message, then a full-stop character approximately every 1/10th second and writes `Done` when it completes.

Here is the source code:

```pascal
program Timed;

{$APPTYPE CONSOLE}

uses
  SysUtils, Windows;

var
  TimeToRun: Integer; // time program is to run for in ms
  StartTick: Integer; // tick count when program starts
  TickNow: Integer;   // tick count during each program loops
begin
  TimeToRun := 1000 * StrToIntDef(ParamStr(1), 5);
  ExitCode := 0;
  WriteLn('TIMED: Running for ', TimeToRun div 1000, ' seconds');
  StartTick := GetTickCount;
  repeat
    TickNow := GetTickCount;
    Sleep(100);
    Write('.');
  until TickNow - StartTick >= TimeToRun;
  WriteLn;
  WriteLn('Done');
end.
```

## Echoer

Usage:

```pascal
Echoer [<prefix>] u]
```

Where:

* `<prefix>` - Prefix text. This text must be quoted if it contains spaces.
* `-u` - Output in Unicode.

This program reads lines of text from standard input, prepends a prefix to each line then writes the modified text to standard output.

If no prefix is provided on the command line then the prefix defaults to the "`>`" character. Input must always be ANSI text and output is also ANSI text unless the `-u` switch is used, when output is in Unicode. Unicode output is always in UCS-2 little endian format with no byte order mark.

Some housekeeping information is written to standard error. This information is also written in Unicode when the `-u` switch is used.

Here is the source code:

```pascal
program Echoer;

{$APPTYPE CONSOLE}

uses
  Windows, SysUtils;

{$IF not Declared(UnicodeString)}
type
  UnicodeString = WideString;
{$IFEND}

{ Emulates C std lib stdout value by returning appropriate Windows handle }
function StdOut: Integer;
begin
  Result := Windows.GetStdHandle(STD_OUTPUT_HANDLE);
end;

{ Emulates C std lib stderr value by returning appropriate Windows handle }
function StdErr: Integer;
begin
  Result := Windows.GetStdHandle(STD_ERROR_HANDLE);
end;

{ Writes an Ansi string to an output "file" }
procedure WriteStr(Handle: THandle; const S: AnsiString); overload;
var
  Dummy: DWORD;
begin
  Windows.WriteFile(Handle, Pointer(S)^, Length(S), Dummy, nil);
end;

{ Writes a Unicode string to an output "file" }
procedure WriteStr(Handle: THandle; const S: UnicodeString); overload;
var
  Dummy: DWORD;
begin
  Windows.WriteFile(
    Handle, Pointer(S)^, Length(S) * SizeOf(WideChar), Dummy, nil
  );
end;

{ Writes an Ansi string followed by a newline to an output "file"}
procedure WriteStrLn(Handle: THandle; const S: AnsiString); overload;
begin
  WriteStr(Handle, S + #13#10);
end;

{ Writes a Unicode string followed by a newline to an output "file"}
procedure WriteStrLn(Handle: THandle; const S: UnicodeString); overload;
begin
  WriteStr(Handle, S + #13#10);
end;

procedure WriteLine(Handle: THandle; const S: AnsiString; AsUnicode: Boolean);
begin
  if AsUnicode then
    WriteStrLn(Handle, UnicodeString(S))
  else
    WriteStrLn(Handle, S);
end;

function StrToAnsiStr(const S: string): AnsiString;
{$IFDEF UNICODE}
var
  Bytes: TBytes;
{$ENDIF}
begin
  {$IFDEF UNICODE}
  Bytes := TEncoding.Default.GetBytes(S);
  SetLength(Result, Length(Bytes));
  if Length(Bytes) > 0 then
    Move(Pointer(Bytes)^, Pointer(Result)^, Length(Bytes));
  {$ELSE}
  Result := S;
  {$ENDIF}
end;

var
  Prefix: AnsiString;
  Line: AnsiString;
  Count: Integer;
  ProgName: AnsiString;
  WantUnicode: Boolean;

begin
  // Parse command line
  ProgName := StrToAnsiStr(ExtractFileName(ParamStr(0)));
  if ParamStr(1) <> '-u' then
    Prefix := StrToAnsiStr(ParamStr(1))
  else
    Prefix := _;
  if Prefix = _ then
    Prefix := '>';
  WantUnicode := ((ParamCount = 2) and (ParamStr(2) = '-u'))
    or ((ParamCount = 1) and (ParamStr(1) = '-u'));

  // Write intro text to stderr
  WriteLine(StdErr, ProgName + ' - Starting', WantUnicode);
  WriteLine(
    StdErr, ProgName + ' - Using prefix: "' + Prefix + '"', WantUnicode
  );

  // Read lines of Ansi text from stdin and copy to stdout with prefix
  Count := 0;
  while not EOF do
  begin
    Inc(Count);
    ReadLn(Line);
    WriteLine(StdOut, Prefix + Line, WantUnicode);
  end;

  // Write closing text to stderr
  WriteLine(
    StdErr,
    ProgName + ' - ' + StrToAnsiStr(IntToStr(Count)) + ' lines written',
    WantUnicode
  );
  WriteLine(StdErr, ProgName + ' - Finished', WantUnicode);
end.
```

## Links

* [Appendix 1](./Appendix1.md)
* [Appendicies](../Appendices.md)
