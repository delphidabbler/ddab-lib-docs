# [Console Application Runner Classes](../../ConsoleApp.md) Example 12: Handling Unicode output from console applications

> This demo uses classes from the [_PJPipe_](../../IOUtils/API/PJPipe.md), [_PJPipeFilters_](../../IOUtils/API/PJPipeFilters.md) & [_PJFileHandle_](../../IOUtils/API/PJFileHandle.md). These units are included in the [I/O Utitlity Classes](../../IOUtils/API.md) download.

If you are not using a Unicode version of Delphi the _UnicodeString_ type must be declared as _WideString_. Adding the [_PJPipeFilters_](../../IOUtils/API/PJPipeFilters.md) unit to the uses statement in the interface will do this for you.

It is possible that you may come across a console application that writes Unicode format text to standard output. In this case, and if you need to read and format the output via a pipe you need to handle it differently than the case where the text is ANSI.

The [_TPJUnicodeBMPPipeFilter_](../../IOUtils/API/TPJUnicodeBMPPipeFilter.md) class, from [PJPipeFilters.pas](../../IOUtils/API/PJPipeFilters.md), makes this easy, providing the text is all in the Unicode basic multilingual plane. For example, to convert [Example 8](../Examples/Example8.md) to handle Unicode all that needs to be done is to replace occurences of [_TPJAnsiSBCSPipeFilter_](../../IOUtils/API/TPJAnsiSBCSPipeFilter.md) with [_TPJUnicodeBMPPipeFilter_](../../IOUtils/API/TPJUnicodeBMPPipeFilter.md) and change the type of the string parameter in [_OnLineEnd_](../../IOUtils/API/TPJUnicodeBMPPipeFilter-OnLineEnd.md) event handlers from _AnsiString_ to _UnicodeString_.

This example is similar to example [Example 8](../Examples/Example8.md): it send the contents of a text file to the console application's standard input and redirects the output to a pipe, displaying the text read from the pipe in a memo control. The differences this time are that the output is Unicode and we will only redirect standard output, ignoring standard error. If you want to redirect standard error look again at [Example 8](../Examples/Example8.md) and it should be obvious how to do this.

> We use our old friend `Echoer.exe` again. Running `Echoer` with the `-u` switch causes the program to write its output in Unicode. Note though that input must still be ANSI text.

Start a new Delphi GUI application. Drop a _TMemo_ and a _TButton_ on the form and add [_PJConsoleApp_](../API/PJConsoleApp.md), [_PJPipe_](../../IOUtils/API/PJPipe.md), [_PJFileHandle_](../../IOUtils/API/PJFileHandle.md) and [_PJPipeFilters_](../../IOUtils/API/PJPipeFilters.md) to the uses statement in the interface section.

Now add the following code to the private section of the form class:

```pascal
  private
    fOutFilter: TPJUnicodeBMPPipeFilter;
    procedure LineEndHandler(Sender: TObject; const Line: UnicodeString);
    procedure WorkHandler(Sender: TObject);
```

Notice that the type of the _LineEndHandler_'s _Line_ parameter is now _UnicodeString_. Implement _LineEndHandler_ and _WorkHandler_ as follows:

```pascal
procedure TForm1.LineEndHandler(Sender: TObject; const Line: UnicodeString);
begin
  Memo1.Lines.Add(Line);
end;

procedure TForm1.WorkHandler(Sender: TObject);
begin
  fOutFilter.ReadPipe;
  Application.ProcessMessages;
end;
```

Just as we saw in [Example 8](../Examples/Example8.md), _LineEndHandler_ adds the line of text passed to it in the _Line_ parameter to the memo control. _WorkHandler_ causes the output filter to read the pipe and calls _Application.ProcessMessages_ as usual.

Now create an _OnClick_ event handler for the button control as follows:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  App: TPJConsoleApp;
  InFile: TPJFileHandle;
begin
  InFile := nil;
  App := nil;
  fOutFilter := TPJUnicodeBMPPipeFilter.Create(TPJPipe.Create, True);
  try
    fOutFilter.OnLineEnd := LineEndHandler;
    InFile := TPJFileHandle.Create(
      'Input.txt', fmOpenRead or fmShareDenyNone
    );
    App := TPJConsoleApp.Create;
    App.StdIn := InFile.Handle;
    App.StdOut := fOutFilter.Pipe.WriteHandle;
    App.TimeSlice := 5;
    App.OnWork := WorkHandler;
    App.CommandLine := 'Echoer ">>> " -u';
    if not App.Execute then
      raise Exception.CreateFmt(
        'Error %X: %s', [App.ErrorCode, App.ErrorMessage]
      );
  finally
    App.Free;
    InFile.Free;
    FreeAndNil(fOutFilter);
  end;
end;
```

First we create the output pipe filter using [_TPJUnicodeBMPPipeFilter_](../../IOUtils/API/TPJUnicodeBMPPipeFilter.md) and assign our [_OnLineEnd_](../../IOUtils/API/TPJUnicodeBMPPipeFilter-OnLineEnd.md) event handler. The output pipe is created on the fly in the filter object's constructor and we give ownership of the pipe to the filter object by passing `True` as the constructor's second parameter.

Next we open the input file for reading. Replace `Input.txt` with a reference to a suitable ANSI text file. After creating the [_TPJConsoleApp_](../API/TPJConsoleApp.md) object the [inheritable](../InheritableHandles.md) file handle is assigned to the console application object's [_StdIn_](../API/TPJCustomConsoleApp-StdIn.md) property to redirect the file to the console application's standard input.

Now the console application's standard output is set to write to the output pipe by assigned the pipe's write handle to the console application object's [_StdOut_](../API/TPJCustomConsoleApp-StdOut.md) property. We get the pipe handle from the output filter's [_Pipe_](../../IOUtils/API/TPJPipeFilter-Pipe.md) property, which gives access to the pipe created in the filter object's constructor.

The next couple of lines have been seen many times before: we set a suitably short time slice and assign the [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event handler.

The next two lines execute the console application. This time we are setting the [_CommandLine_](../API/TPJCustomConsoleApp-CommandLine.md) property and then calling a parameterless version of the [_Execute_](../API/TPJCustomConsoleApp-Execute.md) method. In previous examples we have passed the command line as a parameter to [_Execute_](../API/TPJCustomConsoleApp-Execute.md). Both are equivalent, we're just using the property based approach here to demonstrate it. Notice we pass the `-u` switch to `Echoer` to get the Unicode output.

The remainder of the method just tidies up. Freeing _fOutFilter_ also flushes its text buffer and may cause the [_OnLineEnd_](../../IOUtils/API/TPJUnicodeBMPPipeFilter-OnLineEnd.md) event to fire one last time.

Compile the program and run it. Click the button and watch the output of the program appear in the memo control.

> If you want to assure yourself that `Echoer` run with the `-u` switch does indeed output Unicode then run it from a command line window using the following command:

````batch
echoer -u <input.txt >output.txt
````

where `input.txt` is a valid ANSI text file (you may need to provide a path).

If you open `output.txt` in a text editor like _NotePad++_ that shows the encoding you should see it reported as Unicode little endian (or UCS-2 LE) with no byte order mark.

Run the command again, this time without the `-u` switch, and the text file should be now be reported as ANSI text.

## Links

* [Next example](./Example13.md)
* [Previous example](./Example11.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
