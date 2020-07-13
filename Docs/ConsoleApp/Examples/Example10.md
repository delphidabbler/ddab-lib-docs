# [Console Application Runner Classes](../../ConsoleApp.md) Example 10: Using TPJConsoleApp from console applications

All our example applications so far have been Windows GUI applications. You shouldn't get the impression that you can only use [_TPJConsoleApp_](../API/TPJConsoleApp.md) with GUI applications - it works perfectly well with console applications and this example will show.

Start a new Delphi console application. Now create a new unit in the project and save it as `UMain.pas`. Add the following class declaration to the new unit's interface:

```pascal
type
  TMain = class(TObject)
  private
    fVisible: Boolean;
    fNewConsole: Boolean;
    fTitle: string;
    procedure WorkHandler(Sender: TObject);
    procedure ParseCommandLine;
  public
    procedure Execute;
  end;
```

This class parses the program's command line then uses [_TPJConsoleApp_](../API/TPJConsoleApp.md) to run the `Timed.exe` program from [Appendix 2](../Appendices/Appendix2.md).

> You don't have to use `Timed`. However note we need a program that runs for at least 2 or 3 seconds.

Add the following implementation of _TMain_:

```pascal
uses
  SysUtils, PJConsoleApp;

procedure TMain.Execute;
var
  App: TPJConsoleApp;
begin
  ParseCommandLine;
  App := TPJConsoleApp.Create;
  try
    // Set properties based on parameters
    App.Visible := fVisible;
    App.UseNewConsole := fNewConsole;
    App.ConsoleTitle := fTitle;
    // Set OnWork handler
    App.OnWork := WorkHandler;
    // Run the application
    WriteLn('Starting Timed.exe');
    if not App.Execute('Timed 3') then
      raise Exception.CreateFmt(
        '%X: %s', [App.ErrorCode, App.ErrorMessage]
      );
    WriteLn('Timed.exe completed with exit code: ', App.ExitCode);
  finally
    App.Free;
  end;
end;

procedure TMain.ParseCommandLine;
var
  Param: string;
  Idx: Integer;
begin
  for Idx := 1 to ParamCount do
  begin
    Param := ParamStr(Idx);
    if Param = '-v' then
      fVisible := True
    else if Param = '-n' then
      fNewConsole := True
    else if (Param <> _) and (Param[1] <> '-') then
      fTitle := Param
    else
      raise Exception.CreateFmt('Unknown parameter "%s"', [Param]);
  end;
end;

procedure TMain.WorkHandler(Sender: TObject);
var
  App: TPJConsoleApp;
begin
  App := Sender as TPJConsoleApp;
  if App.UseNewConsole then
    WriteLn('Waited ', App.ElapsedTime, ' ms for Timed.exe');
end;
```

The _Execute_ method creates a [_TPJConsoleApp_](../API/TPJConsoleApp.md) instance then sets properties based on the parameters passed on the command line. An [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event handler is set before executing the application.

_WorkHandler_ checks to see if the console application is sharing the main program's console. If so the handler does not write any output - this would interfere with text written by the child process. If the child process is displaying in its own console (which could be hidden if the [_Visible_](../API/TPJCustomConsoleApp-Visible.md) property is `False`), then the event handler writes out the elapsed time to the main console.

The _ParseCommandLine_ method checks the command line for valid commands and sets the appropriate field values. Valid parameters are:

| Parameter | Description |
|-----------|-------------|
| `-v` | The child process is visible. If this switch is not provided the child process is not visible. If the child process is displayed in the host program's console this switch is ignored. |
| `-n` | Displays the child process in its own console window. If this switch is not provided the child process outputs to the host's console window. |
| `<title>` | Text to be displayed in the console window's title bar. If not supplied the child process' console window has its default title. Any title is ignored if the child process does not have its own console. Quote any title that contains spaces. |

Now switch back to the project file and enter the following code in the program body:

```pascal
begin
  try
    WriteLn('TPJConsoleApp Example 10');
    with TMain.Create do
      try
        Execute;
      finally
        Free;
      end;
    WriteLn('TPJConsoleApp Example 10: Done');
  except
    on E: Exception do
      WriteLn('ERROR: ', E.Message);
  end;
end.
```

This code simply displays some text before executing the main code in _TMain_ and signing off. The code also handles any exceptions.

Run the application with various parameters and note its behaviour. See the table above for details of the command line parameters.

## Links

* [Next example](./Example11.md)
* [Previous example](./Example9.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
