# [Console Application Runner Classes](../../ConsoleApp.md) Example 5: Terminating an application

In [Example 4](./Example4.md) we learned how to set a maximum time to run for a console application and how to forcibly terminate it if it timed out. Unfortunately it's not always possible to second guess how long an application will need to run, and so we may be forced to set the [_MaxExecTime_](../API/TPJCustomConsoleApp-MaxExecTime.md) property to _INFINITE_. In these cases it may be appropriate to give the user the choice to terminate the process.

[_TPJConsoleApp_](../API/TPJConsoleApp.md) provides the [_Terminate_](../API/TPJCustomConsoleApp-Terminate.md) method for just this purpose. Calling [_Terminate_](../API/TPJCustomConsoleApp-Terminate.md) causes the [_Execute_](../API/TPJCustomConsoleApp-Execute.md) method to return _False_, the [_ErrorCode_](../API/TPJCustomConsoleApp-ErrorCode.md) property to have value `$20000002` ([_cAppErrorTerminated_](../API/Constants.md#capperrorterminated)) and the [_ErrorMessage_](../API/TPJCustomConsoleApp-ErrorMessage.md) property to store a suitable message. If the [_KillTimedOutProcess_](../API/TPJCustomConsoleApp-KillTimedOutProcess.md) property is _False_ the process is actually left executing, just the link between [_TPJConsoleApp_](../API/TPJConsoleApp.md) and the process is broken. However when [_KillTimedOutProcess_](../API/TPJCustomConsoleApp-KillTimedOutProcess.md) is _True_ the application is forcibly terminated.

To check this out, start a new Delphi GUI application and drop two buttons and a checkbox on the form. The first button will be used to execute a console application and the second button will be used to terminate it. Set the second button's _Enabled_ property to _False_ - we will enable it when the console application starts. The check box state will determine the value of the [_KillTimedOutProcess_](../API/TPJCustomConsoleApp-KillTimedOutProcess.md) property.

It should come as no surprise we need a private work handler method of the form class:

```pascal
procedure WorkHandler(Sender: TObject);
```

This time we simply need to keep the GUI interactive while the console application is running, so the implementation is simply:

```pascal
procedure TForm1.WorkHandler(Sender: TObject);
begin
  Application.ProcessMessages;
end;
```

Now add this _OnClick_ event handler for _Button1_ (the button we use to execute the console application):

```pascal
procedure TForm1.Button1Click(Sender: TObject);
begin
  fApp := TPJConsoleApp.Create;
  try
    Button2.Enabled := True;
    fApp.MaxExecTime := INFINITE;
    fApp.KillTimedOutProcess := Checkbox1.Checked;
    fApp.TimeSlice := 200;
    fApp.Visible := True;
    fApp.OnWork := WorkHandler;
    if fApp.Execute('Timed 5') then
      ShowMessage('Application completed normally')
    else
      ShowMessageFmt('Error %X: %s', [fApp.ErrorCode, fApp.ErrorMessage]);
  finally
    Button2.Enabled := False;
    FreeAndNil(fApp);
  end;
end;
```

> We're using `Timed.exe` from [Appendix 2](../Appendices/Appendix2.md) again as the long-running console application.

Finally, add the following _OnClick_ event handler for _Button2_ (that we will use to terminate the application):

```pascal
procedure TForm1.Button2Click(Sender: TObject);
begin
  if Assigned(fApp) then
    fApp.Terminate;
end;
```

Compile and run the application. Leave the check box clear and click the first button to start the console application. Press the terminate button while the the console application is running. You should get a message box showing the error code `$20000002` and a message noting the application has been terminated. The console application should continue to run, but the link to [_TPJConsoleApp_](../API/TPJConsoleApp.md) will have been broken.

Now check the check box and run the console application again, pressing the terminate button. This time the same message should be displayed and the console application should be terminated.

> ***Warning:*** Windows may not clean up normally after forcible termination of an application. This is what happens when an application times out when [_KillTimedOutProcess_](../API/TPJCustomConsoleApp-KillTimedOutProcess.md) is _True_. Look up [_TerminateProcess_](http://msdn.microsoft.com/en-us/library/ms686714.aspx) in the Windows API documentation for further information.

## Links

* [Next example](./Example6.md)
* [Previous example](./Example4.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
