# [Console Application Runner Classes](../../ConsoleApp.md) Example 1: ExecAndWait

***Project:*** [Console Application Runner Classes](../API.md)

You will no doubt have seen a lot of code on the Internet that shows how to execute a console application and wait for it to complete. It will probably look something like this:

```pascal
function ExecAndWait(const CommandLine: string): Boolean;
var
  StartupInfo: Windows.TStartupInfo;     // start-up info passed to process
  ProcessInfo: Windows.TProcessInformation; // info about the process
  ProcessExitCode: Windows.DWord;           // process's exit code
begin
  // Set default error result
  Result := False;
  // Initialise startup info structure to 0, and record length
  FillChar(StartupInfo, SizeOf(StartupInfo), 0);
  StartupInfo.cb := SizeOf(StartupInfo);
  // Execute application commandline
  if Windows.CreateProcess(nil, PChar(CommandLine),
    nil, nil, False, 0, nil, nil,
    StartupInfo, ProcessInfo) then
  begin
    try
      // Now wait for application to complete
      if Windows.WaitForSingleObject(ProcessInfo.hProcess, INFINITE)
        = WAIT_OBJECT_0 then
        // It's completed - get its exit code
        if Windows.GetExitCodeProcess(ProcessInfo.hProcess,
          ProcessExitCode) then
          // Check exit code is zero => successful completion
          if ProcessExitCode = 0 then
            Result := True;
    finally
      // Tidy up
      Windows.CloseHandle(ProcessInfo.hProcess);
      Windows.CloseHandle(ProcessInfo.hThread);
    end;
  end;
end;
```

With the use if infinite waiting for the console application to complete, we can achieve the same result using [_TPJConsoleApp_](../API/TPJConsoleApp.md) as follows:

```pascal
function ExecAndWait2(const CommandLine: string): Boolean;
var
  App: TPJConsoleApp;
begin
  App := TPJConsoleApp.Create;
  try
    App.MaxExecTime := INFINITE;  // don't time out
    App.TimeSlice := INFINITE;    // timeout for WaitForSingleObject
    App.Visible := True;          // ensure we see the app
    if App.Execute(CommandLine) then
      Result := App.ExitCode = 0  // app executed OK � check its exit code
    else
      Result := False;            // app didn't execute
  finally
    App.Free;
  end;
end;
```

This is a little crude - the [_TPJConsoleApp_](../API/TPJConsoleApp.md) class can do a lot better than this. Using code like this isn't recommended.

One problem with the above code is that, if you run the console app from a GUI application, your GUI locks up until the console app completes.

Try it. Using Delphi, create a new GUI application. First copy the above code for _ExecAndWait_ and _ExecAndWait2_ into the form unit's implementation section. Now drop two buttons on the main form and add the following _OnClick_ event handlers:

```pascal
procedure TForm1.Button1Click(Sender: TObject);
begin
  if not ExecAndWait('Timed 3') then  // runs Timed.exe for 3 seconds.
    ShowMessage('Non-zero error code or application could not be executed');
end;

procedure TForm1.Button2Click(Sender: TObject);
begin
  if not ExecAndWait2('Timed 3') then // runs Timed.exe for 3 seconds.
    ShowMessage('Non-zero error code or application could not be executed');
end;
```

Run the application. Click either button. The console application will run. Try switching back to the application while the console application is running. You can't can you?

> We've used an application called `Timed.exe` here that takes a parameter that tells it how many seconds to run. You can use anything suitable. If you want to try `Timed`, its source code is available in [Appendix 2](../Appendices/Appendix2.md).

This behaviour may be what you want, but what if the console app freezes? Your app can't do anything about it. [Example 2](./Example2.md) shows how to let your GUI application "breathe" while the console application executes.

## Links

* [Next example](./Example2.md)
* [Examples contents](../Examples.md)
* [Start page](../../ConsoleApp.md)
