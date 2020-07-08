# [Console Application Runner Classes](../../ConsoleApp.md) Example 3: Indicating progress

It is common to want to display some kind of progress indicator while another application is running. This example shows how to do that using [_TPJConsoleApp_](../API/TPJConsoleApp.md). Our application needs to handle the [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event to get notified whenever the console application yields control in order to update a progress bar.

Start a new Delphi GUI application, drop a progress bar and a button on the form. Set the progress bar's _Max_ property to `10`. As in [Example 2](./Example2.md) we're going to need an [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event handler, so create the private method:

```pascal
procedure WorkHandler(Sender: TObject);
```

This time implement the method as follows:

```pascal
procedure TForm1.WorkHandler(Sender: TObject);
begin
  if ProgressBar1.Position = ProgressBar1.Max then
    ProgressBar1.Position := 0
  else
    ProgressBar1.Position := ProgressBar1.Position + 1;
  Application.ProcessMessages;
end;
```

Now create an _OnClick_ event handler for the button as follows:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  App: TPJConsoleApp;
begin
  App := TPJConsoleApp.Create;
  try
    App.MaxExecTime := INFINITE;  // don't time out
    App.TimeSlice := 100;         // yield to main app every 1/10 second
    App.Visible := True;          // ensure we see the app
    App.OnWork := WorkHandler;    // assign the event handler
    if not App.Execute('Timed 5') then  // run Timed.exe for 5 seconds
      ShowMessage('Failed to run Timed.exe');
  finally
    App.Free;
  end;
end;
```

This is the same code we used in [_Example 2_](./Example2.md) - all the changes are in the [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event handler.

> We're using `Timed.exe` from [Appendix 2](../Appendices/Appendix2.md) again - change it if you wish.

Click the button to run the console application, switch back to the main form and watch the progress bar.

## Links

* [Next example](./Example4.md)
* [Previous example](./Example2.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
