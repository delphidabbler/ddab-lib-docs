# [Console Application Runner Classes](../../ConsoleApp.md) Example 9: Subclassing TPJConsoleApp

> This example requires the [_TPJPipe_](../../IOUtils/API/TPJPipe.md) class from the [PJPipe.pas](../../IOUtils/API/PJPipe.md) unit. The unit is included in the [I/O Utitlity Classes](https://delphidabbler.com/software/ioutils) download.

Most of the previous examples have had to handle events to provide some of the needed functionality. In the later examples they have also had to manipulate pipes. This is all very well, but it does rather clutter up the main form code. There are a couple of alternatives that move the messy code out of the form:

1. Encapsulate all the code in another class that creates a [_TPJConsoleApp_](../API/TPJConsoleApp.md) and supplies the required event handlers. This new class can then provide a simplified interface to the main form.
2. Derive a new class from [_TPJCustomConsoleApp_](../API/TPJCustomConsoleApp.md) and override methods to provide the required functionality.

There are benefits to both approaches. In this example we're going to look only at the latter case and derive a new class from [_TPJCustomConsoleApp_](../API/TPJCustomConsoleApp.md).

Look again at [Example 7](../Examples/Example7.md). In essence what this code does is:

1. Read the data out of _Memo1_.
2. Pass that data to a pipe.
3. Set up an output pipe and stream.
4. Execute the console application.
5. Write the resulting data to _Memo2_.

We can replace this with the following:

1. Read data out of _Memo1_ into an input stream.
2. Create an output stream.
3. Call a method of another object that uses the console application to process the input stream and write the output stream.
4. Write the resulting data to _Memo2_.

This has moved all knowledge of how to load streams into pipes and vice versa out of the form. We can create a descendant of [_TPJCustomConsoleApp_](../API/TPJCustomConsoleApp.md) that performs the task at item 3 above.

In this example we will recreate [Example 7](../Examples/Example7.md) by subclassing [_TPJCustomConsoleApp_](../API/TPJCustomConsoleApp.md).

Start a new Delphi GUI project and add a new unit file, named `UConsoleAppEx.pas`. Add the following code to its interface section:

```pascal
uses
  Classes, PJConsoleApp, PJPipe;

type
  TConsoleAppEx = classTPJCustomConsoleApp-
  private
    fOutPipe: TPJPipe;
    fOutStream: TStream;
  protected
    procedure DoWork; override;
  public
    function Execute(const CmdLine: string; const InStream,
      OutStream: TStream): Boolean;
    // Make protected properties public
    property ErrorCode;
    property ErrorMessage;
    property TimeSlice;
  end;
```

The _Execute_ method replaces the [one in the base class](../API/TPJCustomConsoleApp-Execute.md). It receives the command we are to execute as well as an input stream containing data to be piped to the console process' standard input and a stream to receive data piped from standard output. We also make three required properties public. (All properties of [_TPJCustomConsoleApp_](../API/TPJCustomConsoleApp.md) are protected.) The inherited [_DoWork_](../API/TPJCustomConsoleApp-DoWork.md) method is overridden to read the output pipe. This replaces the [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event handler in [Example 7](../Examples/Example7.md).

_TConsoleAppEx_ is implemented as follows:

```pascal
uses
  SysUtils;

procedure TConsoleAppEx.DoWork;
begin
  fOutPipe.CopyToStream(fOutStream, 0);
end;

function TConsoleAppEx.Execute(const CmdLine: string; const InStream,
  OutStream: TStream): Boolean;
begin
  fOutStream := OutStream;
  InPipe := nil;
  fOutPipe := nil;
  try
    // Set up input pipe and associated with console app stdin
    InPipe := TPJPipe.Create(InStream.Size);
    InPipe.CopyFromStream(InStream, 0);
    InPipe.CloseWriteHandle;
    // Set up output pipe and associate with console app stdout
    fOutPipe := TPJPipe.Create;
    StdIn := InPipe.ReadHandle;
    StdOut := fOutPipe.WriteHandle;
    // Run the application
    Result := inherited Execute(CmdLine);
  finally
    StdIn := 0;
    StdOut := 0;
    FreeAndNil(fOutPipe);
    FreeAndNil(InPipe);
  end;
end;
```

_DoWork_ is straightforward - it copies the current pipe contents to the output stream.

The new _Execute_ method now contains some of the set up code that was in the main form code in [Example 7](../Examples/Example7.md).

First we record a reference to the output stream for later use. Next we create the pipe associated with standard input and copy all the data from _InStream_ to it. The output pipe is then created before associating pipe handles with the console application's standard input and output. Finally, the [_Execute_](../API/TPJCustomConsoleApp-Execute.md) method of the base class is called to execute the console application.

Now switch back to the main form. Add _UConsoleAppEx_ to the uses statement. Now drop a button and two memos on the form then create an _OnClick_ event handler for the button, with the following code:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  App: TConsoleAppEx;
  InStream: TStream;
  OutStream: TStream;
begin
  // Set up i/o streams
  InStream := nil;
  OutStream := nil;
  try
    InStream := TMemoryStream.Create;
    Memo1.Lines.SaveToStream(InStream);
    InStream.Position := 0;
    OutStream := TMemoryStream.Create;
    // Run console app
    App := TConsoleAppEx.Create;
    try
      App.TimeSlice := 2;
      if not App.Execute('Echoer "-->"', InStream, OutStream) then
        raise Exception.CreateFmt(
          'Error %X: %s', [App.ErrorCode, App.ErrorMessage]
        );
    finally
      App.Free;
    end;
    // Read output stream
    OutStream.Position := 0;
    Memo2.Lines.LoadFromStream(OutStream);
  finally
    InStream.Free;
    OutStream.Free;
  end;
end;
```

First a stream is created and the contents of _Memo1_ are copied into it. Next the empty output stream is created. Then we run the console application using our new class. And finally we display the data from the output stream in _Memo2_.

> In the above code `Echoer.exe` from [Appendix 2](../Appendices/Appendix2.md) has been used once again.

Run the application. It should perform exactly the same as [Example 7](../Examples/Example7.md).

## Links

* [Next example](./Example10.md)
* [Previous example](./Example8.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
