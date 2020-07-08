# [Console Application Runner Classes](../../ConsoleApp.md) Example 2: A better ExecAndWait

As noted in [Example 1](./Example1.md), it's often worth letting a GUI program remain interactive - may be to display a progress bar or whatever.

To do this you need to handle [_TPJConsoleApp_](../API/TPJConsoleApp.md)'s [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event.

Start a new Delphi GUI application and, in the form's private section, insert the following new method declaration:

```pascal
procedure WorkHandler(Sender: TObject);
```

Implement the method as follows:

```pascal
procedure TForm1.WorkHandler(Sender: TObject);
begin
  Application.ProcessMessages;
end;
```

Now drop a _TButton_ and add the following code as its _OnClick_ event handler:

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

The main code here is similar to [Example 1](./Example1.md) except that the [_TimeSlice_](../API/TPJCustomConsoleApp-TimeSlice.md) property is now set to `100` rather than `INFINITE` and we have assigned a handler for the [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event. Setting [_TimeSlice_](../API/TPJCustomConsoleApp-TimeSlice.md) forces the console app to yield to the GUI app every 1/10th of a second. When this happens [_TPJConsoleApp_](../API/TPJConsoleApp.md) triggers the [_OnWork_](../API/TPJCustomConsoleApp-OnWork.md) event, and our event handler lets the GUI application receive messages.

Run the program. Try to switch back to the GUI while the console app is running. Unlike in [Example 1](./Example1.md), you can now do it!

> We've used `Timed.exe` from [Appendix 2](../Appendices/Appendix2.md) once again. Substitute another suitable program if you wish, providing it runs for a significant amount of time.

## Links

* [Next example](./Example3.md)
* [Previous example](./Example1.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
