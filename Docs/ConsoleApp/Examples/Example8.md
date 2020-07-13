# [Console Application Runner Classes](../../ConsoleApp.md) Example 8: Capturing console output in a GUI

You may have seen applications (_Inno Setup_ springs to mind), that display output from a console application in real time in a GUI control. In this example we'll see how to use [_TPJConsoleApp_](../API/TPJConsoleApp.md) to do this.

Here is an overview of what we will do:

* Use a console application that processes text on standard input and writes processed output to standard output. We will redirect standard input to a lengthy text file.

> We will use `Echoer.exe` from [Appendix 2](../Appendices/Appendix2.md) once more. Again you can use another application provided it processes ANSI text from standard input and writes ANSI text to standard output.

* Display the console applications' standard output in a memo control. To do this we will redirect standard output to a pipe and read the pipe in an [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event, passing output to a helper class that updates the memo control.

* Do the same thing with the program's standard error output, displaying that in another memo control.

Start a new Delphi GUI application and drop a button and two memo controls. We will display standard output in _Memo1_ and standard error in _Memo2_.

We will use the following helper classes to avoid a considerable amount of complexity in the code:

> All these classes are included in the [I/O Utitlity Classes](../../IOUtils/API.md) download.

* [_TPJPipe_](../../IOUtils/API/TPJPipe.md): to handle pipe i/o and to ensure pipes are opened with [inheritable](../InheritableHandles.md) handles.
* [_TPJFileHandle_](../../IOUtils/API/TPJFileHandle.md): to open the input file with an [inheritable](../InheritableHandles.md) handle.
* [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md): to parse the output from the pipe into lines of text. This class text from a single byte ANSI character set to be output through the pipe.

First add the [_PJConsoleApp_](../API/PJConsoleApp.md), [_PJPipe_](../../IOUtils/API/PJPipe.md), [_PJFileHandle_](../../IOUtils/API/PJFileHandle.md) and [_PJPipeFilters_](../../IOUtils/API/PJPipeFilters.md) units to the uses statement.

Now add the following declarations to the form class' private section:

```pascal
  private
    fErrFilter, fOutFilter: TPJAnsiSBCSPipeFilter;
    procedure ErrLineEndHandler(Sender: TObject; const Line: AnsiString);
    procedure OutLineEndHandler(Sender: TObject; const Line: AnsiString);
    procedure WorkHandler(Sender: TObject);
    procedure CompletionHandler(Sender: TObject);
```

Create an _OnClick_ event handler for the button as follows:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  App: TPJConsoleApp;
  InFile: TPJFileHandle;
  OutPipe, ErrPipe: TPJPipe;
const
  InFileName = 'InputFile.txt';
begin
  fOutFilter := nil;
  fErrFilter := nil;
  OutPipe := nil;
  ErrPipe := nil;
  InFile := nil;
  try
    // Open input file
    InFile := TPJFileHandle.Create(InFileName, fmOpenRead or fmShareDenyNone);

    // Create output pipes: one each for stdout and stderr
    OutPipe := TPJPipe.Create;
    ErrPipe := TPJPipe.Create;

    // Create filter objects used to format text from output pipe into lines
    fOutFilter := TPJAnsiSBCSPipeFilter.Create(OutPipe);
    fOutFilter.OnLineEnd := OutLineEndHandler;
    fErrFilter := TPJAnsiSBCSPipeFilter.Create(ErrPipe);
    fErrFilter.OnLineEnd := ErrLineEndHandler;

    App := TPJConsoleApp.Create;
    try
      // redirect stdin to file and stdout/stderr to pipes
      App.StdIn := InFile.Handle;
      App.StdOut := OutPipe.WriteHandle;
      App.StdErr := ErrPipe.WriteHandle;
      App.OnWork := WorkHandler;
      App.OnComplete := CompletionHandler;
      App.TimeSlice := 1;
      if not App.Execute('Echoer') then
        raise Exception.CreateFmt(
          'Error %X: %s', [App.ErrorCode, App.ErrorMessage]
        );
    finally
      App.Free;
    end;
  finally
    FreeAndNil(fErrFilter);
    FreeAndNil(fOutFilter);
    ErrPipe.Free;
    OutPipe.Free;
    InFile.Free;
  end;
end;
```

Here's what the code does:

* We open a ANSI text file for input with an [inheritable](../InheritableHandles.md) handle using [_TPJFileHandle_](../../IOUtils/API/TPJFileHandle.md). Replace `InputFile.txt` with some suitably long ANSI text file.
* Two default sized pipes are created with [inheritable](../InheritableHandles.md) handles using [_TPJPipe_](../../IOUtils/API/TPJPipe.md).
* Two [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) objects are created to parse the output from the standard output and standard error pipes. Each object is passed the relevant pipe in its constructor and has an event handler set that is called after every complete line of text is read.
* A [_TPJConsoleApp_](../API/TPJConsoleApp.md) object is created that has all of its [_StdIn_](../API/TPJCustomConsoleApp-StdIn.md) handle set to read the input file and its [_StdOut_](../API/TPJCustomConsoleApp-StdOut.md) and [_StdErr_](../API/TPJCustomConsoleApp-StdErr.md) handles set to write to the pipes.
* We assign _WorkHandler_ to the [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event. In this example we also need an [_OnComplete_](../API/TPJCustomConsoleApp-OnComplete.md) event handler - we use _CompletionHandler_ for this.
* A very short [_TimeSlice_](../API/TPJCustomConsoleApp-TimeSlice.md) is used to make output as smooth as possible.
* The application is now executed. This triggers various events where we handle the output.
* Finally we free all the objects. Freeing the [_TPJPipe_](../../IOUtils/API/TPJPipe.md) and [_TPJFileHandle_](../../IOUtils/API/TPJFileHandle.md) objects closes the pipe and file handles respectively.

The [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) and [_OnComplete_](../API/TPJCustomConsoleApp-OnComplete.md) handlers are where we process the piped output from the console application. Implement these like this:

```pascal
procedure TForm1.WorkHandler(Sender: TObject);
begin
  fOutFilter.ReadPipe;
  fErrFilter.ReadPipe;
  Application.ProcessMessages;       // Let the memo controls update
end;

procedure TForm1.CompletionHandler(Sender: TObject);
begin
  fOutFilter.Flush;
  fErrFilter.Flush;
end;
```

_WorkHandler_ calls the [_ReadPipe_](../../IOUtils/API/TPJAnsiSBCSPipeFilter-ReadPipe.md) methods of the two [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) objects. This method simpy copies all available data from the associated pipe and processes it. Importantly, _WorkHandler_ also calls _Application.ProcessMessages_ to enable the memo controls to update.

_CompletionHandler_ causes the [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) objects to flush any remaining text from their internal buffers, ensuring it gets written to the memo controls.

So far we haven't seen how the memo controls actually get updated. This is done in the final piece of code, and that's the implementation of the [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) objects' [_OnLineEnd_](../../IOUtils/API/TPJAnsiSBCSPipeFilter-OnLineEnd.md) event handlers:

```pascal
procedure TForm1.OutLineEndHandler(Sender: TObject; const Line: AnsiString);
begin
  Memo1.Lines.Add(string(Line));
end;

procedure TForm1.ErrLineEndHandler(Sender: TObject; const Line: AnsiString);
begin
  Memo2.Lines.Add(string(Line));
end;
```

These events are triggered once for each complete line of text that the [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) read from the pipes. The events are also triggered for any remaining text when the application ends (in the calls to the [_Flush_](../../IOUtils/API/TPJAnsiSBCSPipeFilter-Flush.md) method). Each event is handled simply by adding the line of text to the appropriate memo control.

Run the application and watch the output appear in the two memo controls.

## A shortened version

The code above is longer than it needs to be in order to make it clear what exactly is happening in the hope that this makes the code easier to understand.

[_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) is able to take ownership of any pipe passed to its constructor so that the pipe is freed when the filter object is freed. The object also exposes a [_Pipe_](../../IOUtils/API/TPJPipeFilter-Pipe.md) property to provide access to the wrapped pipe. This means we don't need the _OutPipe_ and _ErrPipe_ local variables.

The _Button1Click_ event handler can be shortened to:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  App: TPJConsoleApp;
  InFile: TPJFileHandle;
const
  InFileName = 'InputFile.txt';
begin
  fOutFilter := nil;
  fErrFilter := nil;
  InFile := nil;
  try
    InFile := TPJFileHandle.Create(InFileName, fmOpenRead or fmShareDenyNone);

    fOutFilter := TPJAnsiSBCSPipeFilter.Create(TPJPipe.Create, True);
    fOutFilter.OnLineEnd := OutLineEndHandler;
    fErrFilter := TPJAnsiSBCSPipeFilter.Create(TPJPipe.Create, True);
    fErrFilter.OnLineEnd := ErrLineEndHandler;

    App := TPJConsoleApp.Create;
    try
      App.StdIn := InFile.Handle;
      App.StdOut := fOutFilter.Pipe.WriteHandle;
      App.StdErr := fErrFilter.Pipe.WriteHandle;
      App.OnWork := WorkHandler;
      App.OnComplete := CompletionHandler;
      App.TimeSlice := 1;
      if not App.Execute('Echoer') then
        raise Exception.CreateFmt(
          'Error %X: %s', [App.ErrorCode, App.ErrorMessage]
        );
    finally
      App.Free;
    end;
  finally
    FreeAndNil(fErrFilter); // frees pipe object and closes pipe handles
    FreeAndNil(fOutFilter); // frees pipe object and closes pipe handles
    InFile.Free;
  end;
end;
```

The pipe objects are created on the fly in the [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) [constructor](../../IOUtils/API/TPJPipeFilter-Create.md) calls. The optional second `True` parameter tells the filter object to free the pipe when it is destroyed. We use the [_Pipe_](../../IOUtils/API/TPJPipeFilter-Pipe.md) property of the filter to access the pipe's [_WriteHandle_](../../IOUtils/API/TPJPipe-WriteHandle.md) when setting the console application object's [_StdOut_](../API/TPJCustomConsoleApp-StdOut.md) and [_StdIn_](../API/TPJCustomConsoleApp-StdIn.md) properties.

The is one further bit of slimming down we can do, and that is to remove the console application object's [_OnComplete_](../API/TPJCustomConsoleApp-OnComplete.md) event handler. We can do this because [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) instance automatically calls the [_Flush_](../../IOUtils/API/TPJAnsiSBCSPipeFilter-Flush.md) method when the object is being destroyed. This causes the [_OnLineEnd_](../../IOUtils/API/TPJAnsiSBCSPipeFilter-OnLineEnd.md) event handler to be called with any remaining text. Therefore the explicit call to [_Flush_](../../IOUtils/API/TPJAnsiSBCSPipeFilter-Flush.md) in the [_OnComplete_](../API/TPJCustomConsoleApp-OnComplete.md) handler is redundant.

## Links

* [Next example](./Example9.md)
* [Previous example](./Example7.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
