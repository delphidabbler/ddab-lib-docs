# TPJConsoleApp class

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

## Description

This class is designed to be used to control the execution of child console application processes. The class provides facilities to redirect the console process' standard input, output and error handles. The application's execution can be given a time-out and can be time sliced to allow progress to be reported and redirected output to be handled while the console application continues to execute. Security levels and environment blocks can be customised. Errant processes can be terminated. Finally, the program's exit code is made available.

_TPJConsoleApp_ descends from [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md). The only differences are that [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md) declares all properties and events as protected whereas _TPJConsoleApp_ makes them all public.

### Methods

| Method | Description |
|--------|-------------|
| [_Execute_](./TPJCustomConsoleApp-Execute.md) | Executes the console application. |
| [_Terminate_](./TPJCustomConsoleApp-Terminate.md) | Attempts to terminate the console application process. |

### Properties

| Property | Description |
|----------|-------------|
| [_CommandLine_](./TPJCustomConsoleApp-CommandLine.md) | Command line used to execute a console application. |
| [_ConsoleColors_](./TPJCustomConsoleApp-ConsoleColors.md) | Foreground and background colours used in console window. |
| [_ConsoleTitle_](./TPJCustomConsoleApp-ConsoleTitle.md) | Title to be displayed in any new console window. |
| [_CurrentDir_](./TPJCustomConsoleApp-CurrentDir.md) | Application's current directory.|
| [_ElapsedTime_](./TPJCustomConsoleApp-ElapsedTime.md) | Approximate time in milliseconds since the console application began executing. |
| [_Environment_](./TPJCustomConsoleApp-Environment.md) | Pointer to the environment block used by the console application. |
| [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) | Provides information about any error that occurred while attempting to run a console application. |
| [_ErrorMessage_](./TPJCustomConsoleApp-ErrorMessage.md) | Error message corresponding to any non-zero value of [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md). |
| [_ExitCode_](./TPJCustomConsoleApp-ExitCode.md) | Exit code returned by the console application on completion. |
| [_KillTimedOutProcess_](./TPJCustomConsoleApp-KillTimedOutProcess.md) | Indicates whether timed-out processes should be terminated or left running. |
| [_MaxExecTime_](./TPJCustomConsoleApp-MaxExecTime.md) | Maximum permitted execution time of the console application. |
| [_Priority_](./TPJCustomConsoleApp-Priority.md) | Priority with which the console application is started. |
| [_ProcessAttrs_](./TPJCustomConsoleApp-ProcessAttrs.md) | Specifies security and inheritance attributes for the console application process. |
| [_ProcessInfo_](./TPJCustomConsoleApp-ProcessInfo.md) | Provides process information for the executing console application. |
| [_ScreenBufferSize_](./TPJCustomConsoleApp-ScreenBufferSize.md) | Size of console's screen buffer. |
| [_StdErr_](./TPJCustomConsoleApp-StdErr.md) | The console application's standard error handle. |
| [_StdIn_](./TPJCustomConsoleApp-StdIn.md) | The console application's standard input handle. |
| [_StdOut_](./TPJCustomConsoleApp-StdOut.md) | The console application's standard output handle. |
| [_ThreadAttrs_](./TPJCustomConsoleApp-ThreadAttrs.md) | Security and inheritance attributes for the console application's primary thread. |
| [_TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) | Length of each time slice for a timed sliced console application. |
| [_TimeToLive_](./TPJCustomConsoleApp-TimeToLive.md) | Amount of time a console application has left to run before timing out. |
| [_UnicodeEnvironment_](./TPJCustomConsoleApp-UnicodeEnvironment.md) [v3.1] | Determines whether environment block referenced by [_Environment_](./TPJCustomConsoleApp-Environment.md) is in Unicode or ANSI. |
| [_UseNewConsole_](./TPJCustomConsoleApp-UseNewConsole.md) | Determines if a console application opens a new console window when run.|
| [_Visible_](./TPJCustomConsoleApp-Visible.md) | Determines whether the console application is to be displayed. |
| [_WindowPosition_](./TPJCustomConsoleApp-WindowPosition.md) | Position of console window on screen. |
| [_WindowSize_](./TPJCustomConsoleApp-WindowSize.md) | Size of console window. |

### Events

| Event | Description |
|-------|-------------|
| [_OnComplete_](./TPJCustomConsoleApp-OnComplete.md) | Triggered when an application completes or times out. |
| [_OnStart_](./TPJCustomConsoleApp-OnStart.md) | Triggered after a console application process is created and just before it starts executing. |
| [_OnWork_](./TPJCustomConsoleApp-OnWork.md) | Triggered when the executing application yields control to this class. Permits necessary work to be completed. |

## See Also

* [Classes List](./Classes.md)
* [Programmers' Guide](../API.md)
