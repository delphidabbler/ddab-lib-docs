# Console Application Runner Classes FAQ

This page has some frequently asked questions about the DelphiDabbler [Console Application Runner Classes](https://delphidabbler.com/software/consoleapp). You can also try the class' **[documentation](../Docs/ConsoleApp.md)**.

## Contents

1. [Why am I getting an access violation when running code that uses TPJConsoleApp compiled with with Delphi 2009 (and later)?](#faq-1)
2. [Does TPJConsoleApp handle Unicode output from console applications correctly?](#faq-2)
3. [In the command shell running "MyApp.exe >out.txt" redirects MyApp's output to out.txt. Why doesn't this command redirect when run with TPJConsoleApp?](#faq-3)
4. [In the command shell I can pipe data between applications. How can I do this with TPJConsoleApp?](#faq-4)
5. [How do I create or open a file with an inheritable handle?](#faq-5)

----

## FAQ 1

**Why am I getting an access violation when running code that uses TPJConsoleApp compiled with with Delphi 2009 (and later)?**

This is because Delphi 2009 and later (the "Unicode Delphis") use the Unicode Windows API (earlier versions used the ANSI API). It is a peculiarity of the Unicode implementation of the `CreateProcess` API function (which `[[(Docs.)TPJConsoleApp]]` uses) that causes this access violation. This peculiarity wasn't present in the ANSI version of the function.

> The classes have been updated to work round this problem. You need to update to release 1.0.2 or later.


## FAQ 2

**Does TPJConsoleApp handle Unicode output from console applications correctly?**

There is no straightforward answer to this. Because `TPJConsoleApp` can run any console app it can know nothing about the output of programs it is used to run.

In the case where the program's output is displayed in the console window the question is irrelevant.

If the output is being redirected to a file then the output is a faithful byte by byte copy of the console program output. If the program writes Unicode text then that's what the file will contain.

If output is redirected to the pipe then, again, the actual bytes output by the program are written to the pipe. The programmer is responsible for reading the pipe and must make sure that any structured data is re-assembled correctly. Each time the pipe is read it is possible it may contain an odd number of bytes, which is not valid Unicode. But I stress, it is up to the programmer to handle this - it is not a function of `TPJConsoleApp`.

> Some pipe filter classes are available in the [I/O Utility Classes project](https://delphidabbler.com/software/ioutils), one of which can read Unicode from a pipe correctly. See [this example](../Docs/ConsoleApp/Examples/Example12.md) for details.

## FAQ 3

**In the command shell running `MyApp.exe >out.txt` redirects MyApp's output to `out.txt`. Why doesn't this command redirect when run with `TPJConsoleApp`**

The `>` redirection operator in `MyApp.exe >out.txt` is special to the command shell. The shell interprets it by making `MayApp.exe` write its standard output to `out.txt` instead of the console.

The operator has no meaning outside the command shell. To see this try executing a command line containing the ">" operator via the Windows Run dialog box [Windows Key + R]. It won't work. Using the Windows API to execute such a command also fails: this is what `TPJConsoleApp` does.

`TPJConsoleApp` **can** do redirection, but you have to do a lot of the work yourself that the command shell does behind the scenes. To understand this let's take a look at what the command shell does when it encounters the `>` operator.

First the shell creates a new empty file named `out.txt`. The file is created with an inheritable handle to permit it to be used by a child process. `MyApp.exe` is now executed as a child process of the shell and has its standard output handle redirected to the file handle so that anything written to standard output goes to the file.

We have to do the same to use `TPJConsoleApp` for redirection. First create the file ensuring its handle is inheritable ([FAQ 5](#faq-5) explains how). Assign the file handle to `TPJConsoleApp`'s `StdOut` property. Finally call `Execute` with a command line parameter of `@@MyApp.exe@@`, leaving off the redirection operator part.

Redirection using the `2>` (redirect standard error output) and `<` (redirect standard input) operators is similar. Open the required files for output (standard error) or input (standard input) and assign the (inheritable) handles to `TPJConsoleApp`'s `StdErr` or  `StdIn` properties respectively.


## FAQ 4

**In the command shell I can pipe data between applications. How can I do this with TPJConsoleApp?**

The only way I have found to do this is to run each application in sequence, capturing output via a pipe to a memory stream an feeding that data into the next application, again via a pipe. It's cruder than threads, because it just runs each application in turn and buffers output before feeding to the next application, but I suspect (but don't know) that is what Windows `cmd.exe` does when you use the pipe (`|`) operator. Regardless, I haven't found a way to do this successfully using a separate thread for each application.

To help handle the housekeeping you can use the following class, which needs both the `PJConsoleApp` and `PJPipe` units. Enter the code in a unit named `UConsoleAppChain`.

~~~pascal
unit UConsoleAppChain;

interface

uses
  Classes,
  PJConsoleApp, PJPipe;

type
  TConsoleAppArray = array of TPJConsoleApp;

  // Chains together two or more apps represented by TPJConsoleApp instances
  // passing intermediate data via pipes and memory streams.
  TConsoleAppChain = class(TObject)
  private
    fIntermediateStream: TStream;
    fOutPipe: TPJPipe;
    fInPipe: TPJPipe;
    procedure SourceWork(Sender: TObject);
  public
    constructor Create;
    destructor Destroy; override;
    procedure Execute(const Apps: TConsoleAppArray);
  end;

implementation

uses
  SysUtils;

{ TConsoleAppChain }

constructor TConsoleAppChain.Create;
begin
  inherited Create;
  fIntermediateStream := TMemoryStream.Create;
end;

destructor TConsoleAppChain.Destroy;
begin
  fInPipe.Free;
  fOutPipe.Free;
  fIntermediateStream.Free;
  inherited;
end;

procedure TConsoleAppChain.Execute(const Apps: TConsoleAppArray);
var
  Idx: Integer;
  FirstAppIdx: Integer;
  LastAppIdx: Integer;
begin
  Assert(Length(Apps) >= 2);

  FirstAppIdx := Low(Apps);
  LastAppIdx := High(Apps);

  fIntermediateStream.Size := 0;

  for Idx := FirstAppIdx to LastAppIdx do
  begin
    try
      if Idx > FirstAppIdx then
      begin
        fIntermediateStream.Position := 0;
        fInPipe := TPJPipe.Create(fIntermediateStream.Size);
        fInPipe.CopyFromStream(fIntermediateStream);
        fInPipe.CloseWriteHandle;
        Apps[Idx].StdIn := fInPipe.ReadHandle;
      end;

      if Idx < LastAppIdx then
      begin
        fOutPipe := TPJPipe.Create;
        Apps[Idx].StdOut := fOutPipe.WriteHandle;
        Apps[Idx].OnWork := SourceWork;
      end;

      fIntermediateStream.Size := 0;

      if not Apps[Idx].Execute then
        raise Exception.CreateFmt(
          'Error executing "%0:s": %1:s',
          [Apps[Idx].CommandLine, Apps[Idx].ErrorMessage]
        );
    finally
      FreeAndNil(fOutPipe);
      FreeAndNil(fInPipe);
    end;
  end;
end;

procedure TConsoleAppChain.SourceWork(Sender: TObject);
begin
  fOutPipe.CopyToStream(fIntermediateStream);
end;

end.
~~~

To use, pass an array of `TPJConsoleApp` instances to the `Execute` method, in the order you want them executed. The output of the first instance is used as input to the second and so on. There must be at least two `TPJConsoleApp` instances in the array.

You must set the `StdIn` property of the first app to get the initial data unless it is supplied in any other way. You must also set the `StdOut` property of the last app if you want final output redirected in any way. `TConsoleAppChain` overwrites the remaining `StdIn` and `StdOut` properties, so don't set them. It also sets the `OnWork` event handler of all except the last `TPJConsoleApp` instance to copy output from the pipe to a memory stream.

Each console application except the first must be capable of taking input from standard input. Similarly and each application except the last must write output to standard output.


## FAQ 5

**5: How do I create or open a file with an inheritable handle?**

This question is answered in [Appendix 1](../Docs/ConsoleApp/Appendices/Appendix1.md) of the [Console Application Runner Classes documentation](../Docs/ConsoleApp.md).
