# [Console Application Runner Classes](../../ConsoleApp.md) Example 4: Timing out

All the examples to date have allowed a console application to run for as long as it required. This was done by setting [_TPJConsoleApp_](../API/TPJConsoleApp.md)'s [_MaxExecTime_](../API/TPJCustomConsoleApp-MaxExecTime.md) property to _INFINITE_. In this example we will look at how to set a maximum time for a console application to run and examine what happens when it times out.

The amount of time available for a console application to run is limited by setting the [_MaxExecTime_](../API/TPJCustomConsoleApp-MaxExecTime.md) property (in milliseconds). If this time expires before the console application completes then the [_Execute_](../API/TPJCustomConsoleApp-Execute.md) method returns _False_, the [_ErrorCode_](../API/TPJCustomConsoleApp-ErrorCode.md) property is set to `$20000001` ([_cAppErrorTimeOut_](../API/Constants.md#capperrortimeout)) and the [_ErrorMessage_](../API/TPJCustomConsoleApp-ErrorMessage.md) property stores an explanatory string. However, the console application may keep running. Whether this happens depends on the value of the [_KillTimedOutProcess_](../API/TPJCustomConsoleApp-KillTimedOutProcess.md) property. If it is _True_ the timed-out process is forcibly terminated. When the property is _False_ the process is left executing, but the link between [_TPJConsoleApp_](../API/TPJConsoleApp.md) and the process is broken.

To see all this, start a new Delphi GUI application project and drop a _TEdit_, a _TCheckbox_, a _TButton_ and a _TMemo_ control on the form. Give the _TMemo_ a vertical scroll bar. The edit control will be used to enter the maximum execution time of the program in milliseconds. The check box will set the [_KillTimedOutProcess_](../API/TPJCustomConsoleApp-KillTimedOutProcess.md) property and the memo will be used to display output.

As we've done before add a private work handler method to the form class:

```pascal
procedure WorkHandler(Sender: TObject);
```

and implement the method like this:

```pascal
procedure TForm1.WorkHandler(Sender: TObject);
var
  App: TPJConsoleApp;
begin
  App := Sender as TPJConsoleApp;
  Memo1.Lines.Add(
    Format(
      'Elapsed time: %dms, Time to live: %dms',
      [App.ElapsedTime, App.TimeToLive]
    )
  );
  Application.ProcessMessages;  // keeps GUI interactive
end;
```

Now add the following _OnClick_ event handler for the button:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
var
  App: TPJConsoleApp;
begin
  App := TPJConsoleApp.Create;
  try
    App.MaxExecTime := StrToInt(Edit1.Text);
    App.KillTimedOutProcess := Checkbox1.Checked;
    App.TimeSlice := 200;
    App.Visible := True;
    App.OnWork := WorkHandler;
    if App.Execute('Timed 5') then
      Memo1.Lines.Add('Application completed normally')
    else
      Memo1.Lines.Add(App.ErrorMessage)
  finally
    App.Free;
  end;
end;
```

> Again, `Timed.exe` from [Appendix 2](../Appendices/Appendix2.md) is being used as the console application, set to run for five seconds.

Run the program and enter a maximum execution time that is less than the time the console program will run for (`3000` is good if using `Timed`). Leave the checkbox unchecked. Now click the button to execute the console application. Every 1/5th second the memo control will be updated with the time the program has been running and the maximum time left to run ("time to live"). Once the time to live value hits zero the program will time out and the resulting error message will be displayed in the memo control. Notice that the console application will continue to run.

Now check the check box and repeat the process. Once again the program should time out, but this time the console application will be terminated.

Finally, set the maximum execution time to be longer than the console application will run (`6000` is good if using `Timed`). Click the button to run the console application. The memo will be updated as before until the console application completes. Normal completion will be reported in the memo.

> ***Warning:*** Windows may not clean up normally after forcible termination of an application. This is what happens when an application times out when [_KillTimedOutProcess_](../API/TPJCustomConsoleApp-KillTimedOutProcess.md) is _True_. Look up [_TerminateProcess_](http://msdn.microsoft.com/en-us/library/ms686714.aspx) in the Windows API documentation for further information.

## Links

* [Next example](./Example5.md)
* [Previous example](./Example3.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
