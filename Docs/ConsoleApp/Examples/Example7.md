# [Console Application Runner Classes](../../ConsoleApp.md) Example 7: Redirecting standard i/o using pipes

As useful as redirecting files can be (see [Example 6](./Example6.md)), it is not always very convenient for our application to have to exchange data with a console application by writing input data to a file and then reading a processed file. It is much more useful if we can pass the raw data directly to a console app for processing and to read the processed data back from the console application. We can do this using pipes. It's more convoluted than using files, but worth it.

To redirect a console application's input and output we need two pipes:

* The first pipe is used to send data to the console application's standard input. Our application uses the pipe's write handle to write data to the pipe. We set [_TPJConsoleApp.StdIn_](../API/TPJCustomConsoleApp-StdIn.md) to the pipe's read handle to enable the console application to read the data from the pipe.

* The second pipe is used to read data from the console application's standard output. We set [_TPJConsoleApp.StdOut_](../API/TPJCustomConsoleApp-StdOut.md) to the pipe's write handle and we read the data using the read handle.

The read handle of the first pipe and the write handle of the second pipe must be [inheritable](../InheritableHandles.md).

Because working with pipes can be quite complicated we will use the [_TPJPipe_](../../IOUtils/API/TPJPipe.md) helper class to help simplify things. This class simplifies peeking, reading and writing pipes but and can also create pipe handles that are  [inheritable](../InheritableHandles.md).

> [_TPJPipe_](../../IOUtils/API/TPJPipe.md) is included in the [I/O Utitlity Classes](../../IOUtils/API.md) download in `PJPipe.pas`.

To see the code working, create a new Delphi GUI application and drop a button and two memos on the form. As with [Example 6](./Example6.md), _Memo1_ will receive text to be processed and _Memo2_ will display the results.

Make sure that the uses statement includes [_PJConsoleApp_](../API/PJConsoleApp.md) and [_PJPipe_](../../IOUtils/API/PJPipe.md) then create an _OnClick_ event handler for the button as follows:

Add the following code to the form class' private section:

```pascal
  private
    fOutPipe: TPJPipe;
    fOutStream: TStream;
    procedure WorkHandler(Sender: TObject);
```

Here, _fOutPipe_ is a the [_TPJPipe_](../../IOUtils/API/TPJPipe.md) object used to pipe processed data from the console application and _fOutStream_ is a stream that receives data from _fOutPipe_. _WorkHandler_ is an [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event handler that is implemented like this:

```pascal
procedure TForm1.WorkHandler(Sender: TObject);
begin
  fOutPipe.CopyToStream(fOutStream, 0);
end;
```

This handler simply copies all available data from the output pipe to the output stream. We can't just wait until the program is over before reading all the data from the pipe, because we don't know the size needed for the output pipe or the amount of data written to it in one time slice. It is possible that the data will overflow the pipe. The secret is to make the [_TimeSlice_](../API/TPJCustomConsoleApp-TimeSlice.md) property of [_TPJConsoleApp_](../API/TPJConsoleApp.md) small enough, and create the output pipe big enough, to ensure that the console application never fills the pipe between time slices. Experimentation may be required.

Now create an _OnClick_ event handler for the button and complete it as follows:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  App: TPJConsoleApp;
  Text: string;
  InPipe: TPJPipe;
begin
  fOutStream := nil;
  fOutPipe := nil;
  // Write memo 1 contents as Ansi text into read pipe. Must be ANSI text
  // because Echoer.exe requires Ansi input.
  Text := Memo1.Text;
  InPipe := TPJPipe.Create(Length(Text));
  try
    {$IFDEF UNICODE}
    InPipe.WriteBytes(TEncoding.Default.GetBytes(Text));
    {$ELSE}
    InPipe.WriteData(PChar(Text)^, Length(Text));
    {$ENDIF}
    InPipe.CloseWriteHandle;
    // Create out pipe and stream that receives out pipe's data
    fOutPipe := TPJPipe.Create;
    fOutStream := TMemoryStream.Create;
    // Execute the application
    App := TPJConsoleApp.Create;
    try
      App.TimeSlice := 2; // forces more than one OnWork event
      App.OnWork := WorkHandler;
      App.StdIn := InPipe.ReadHandle;
      App.StdOut := fOutPipe.WriteHandle;
      if not App.Execute('Echoer "--> "') then
        raise Exception.CreateFmt(
          'Error %X: %s', [App.ErrorCode, App.ErrorMessage]
        );
    finally
      App.Free;
    end;
    // Load data from output stream into memo 2: Echoer.exe writes output as
    // ANSI text. OK on Unicode Delphis because following LoadFromStream call
    // defaults to Default (ANSI) encoding if no encoding specified.
    fOutStream.Position := 0;
    Memo2.Lines.LoadFromStream(fOutStream);
  finally
    FreeAndNil(InPipe);
    FreeAndNil(fOutPipe);
    FreeAndNil(fOutStream);
  end;
end;
```

First of all we create the input pipe of the required size and write the contents of _Memo1_ to it. We call the pipe's [_CloseWriteHandle_](../../IOUtils/API/TPJPipe-CloseWriteHandle.md) method when all the data is written to it. This effectively signals end-of-file on the pipe. Without this the console application would endlessly wait for more data when all the pipe data had been read.

Next we create the output pipe (with default size) and the stream to receive output. As we have seen, the pipe's data is copied to the stream in _WorkHandler_. It is because they are used in this separate method that we declare _fOutPipe_ and _fOutStream_ as fields of the class rather than as local variables of _Button1Click_.

Now we choose a small value for [_TimeSlice_](../API/TPJCustomConsoleApp-TimeSlice.md), and set the [_StdIn_](../API/TPJCustomConsoleApp-StdIn.md) and [_StdOut_](../API/TPJCustomConsoleApp-StdOut.md) properties to the appropriate pipe handles before executing the application.

Finally we load _Memo2_ from the output stream.

>
Once again this example uses the `Echoer.exe` console application from [Appendix 2](../Appendices/Appendix2.md). Any programs that reads ANSI text from standard input and writes ANSI text to standard output can be substituted.

Run the program. Type some text in _Memo1_ and click the button to see the processed text appear in _Memo2_, this time without writing any intermediate files.

## Links

* [Next example](./Example8.md)
* [Previous example](./Example6.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
