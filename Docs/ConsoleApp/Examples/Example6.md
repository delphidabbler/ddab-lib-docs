# [Console Application Runner Classes](../../ConsoleApp.md) Example 6: Redirecting standard i/o using files

Console applications are often used with redirected input and output. It is quite common for a console application to process content read from standard input and to write the processed data to standard output. When we want to process files we must redirect the input file to standard input and redirect standard output to an output file.

Redirection from the command line is done using the `<` and `>` redirection operators (and similar). For example, to get `MyApp.exe` to read `In.txt` and write `Out.txt` we would use:

```pascal
MyApp <In.txt >Out.txt
```

When redirecting programmatically we can't use `>` and `<` on the command line, but must instead open handles to the files and pass those handles to Windows. Furthermore, on NT systems, the file handles must be [inheritable](../InheritableHandles.md).

[_TPJConsoleApp_](../API/TPJConsoleApp.md) provides properties [_StdIn_](../API/TPJCustomConsoleApp-StdIn.md), [_StdOut_](../API/TPJCustomConsoleApp-StdOut.md) and [_StdErr_](../API/TPJCustomConsoleApp-StdErr.md) to implement redirection. Simply assign an [inheritable](../InheritableHandles.md) handle to one or more of these properties to redirect standard input, standard output and standard error respectively.

To demonstrate this we need a console application that processes text from standard input and writes the processed text to standard output.

>
This example uses `Echoer.exe` to process the text. The source code for `Echoer` can be found in [Appendix 2](../Appendices/Appendix2.md). If you have a suitable alternative application substitute it in the code below.

Note that `Echoer` expects to receive ANSI text on standard input and writes ANSI text to standard output. Any alternative application must do the same.

Start a new GUI application and drop a button and two memos on the main form. The text to be processed will be entered in _Memo1_. We will then write the memo content to an ANSI text file, process the file using `Echoer.exe` which will write an output file, then load that file into _Memo2_.

We will use the helper class [_TPJFileHandle_](../../IOUtils/API/TPJFileHandle.md) to open the files and obtain their handles. The advantage of using this class is that it opens files with the required inheritable handles. It also closes the handles when the class is freed. You don't have to use the class, but if you don't use must open the required files yourself, ensuring they have inheritable handles. You must also close the handles when they are no longer needed. Some sample code is in [Appendix 1](../Appendices/Appendix1.md).

> [_TPJFileHandle_](../../IOUtils/API/TPJFileHandle.md) is included in the [I/O Utitlity Classes](../../IOUtils/API.md) download in `PJFileHandle.pas`.

First make sure that the uses statement includes [_PJConsoleApp_](../API/PJConsoleApp.md) and [_PJFileHandle_](../../IOUtils/API/PJFileHandle.md) then create an _OnClick_ event handler for the button as follows:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
const
  cInFile = 'Demo6-in.txt';
  cOutFile = 'Demo6-out.txt';
var
  App: TPJConsoleApp;
  InFile, OutFile: TPJFileHandle;
begin
  Memo1.Lines.SaveToFile(cInFile);
  InFile := nil;
  OutFile := nil;
  App := TPJConsoleApp.Create;
  try
    // Open input file and create output file with inheritable handles
    InFile := TPJFileHandle.Create(cInFile, fmOpenRead or fmShareDenyNone);
    OutFile := TPJFileHandle.Create(cOutFile, fmCreate or fmShareExclusive);
    // Redirect app's standard input and standard output
    App.StdIn := InFile.Handle;
    App.StdOut := OutFile.Handle;
    // Run the app without showing console
    App.Visible := False;
    if not App.Execute('Echoer ">>> "') then
      raise Exception.CreateFmt(
        'Error %X: %s', [App.ErrorCode, App.ErrorMessage]
      );
  finally
    OutFile.Free; // closes output file handle
    InFile.Free;  // closes input file handle
    App.Free;
  end;
  // Output file should now contain application output
  Memo2.Lines.LoadFromFile(cOutFile);
end;
```

We have not created an [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event handler for this demo. This is because we expect the text processing application to run very quickly and therefore will have a negligible effect on our application responsiveness.

Run the application, enter some text in _Memo1_ and click the button. The resulting processed file will be displayed in _Memo2_. The files `Eg6-in.txt` and `Eg6-out.txt` will have been created.

>
The sample code above works well with both Unicode and non-Unicode versions of Delphi. This is because the _LoadFromFile_ and _SaveToFile_ methods that the memo controls use for writing and reading the files create ANSI text files in both cases. In non-Unicode Delphis this is the only possible action and in Unicode Delphis it is the default action if no encoding is specified.

## Links

* [Next example](./Example7.md)
* [Previous example](./Example5.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
