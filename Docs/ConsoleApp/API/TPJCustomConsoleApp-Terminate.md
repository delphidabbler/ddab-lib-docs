# Terminate method

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
procedure Terminate;
```

## Description

Attempts to terminate the process.

Calling this method causes the [_Execute_](./TPJCustomConsoleApp-Execute.md) method to return after the next [_OnWork_](./TPJCustomConsoleApp-OnWork.md) event.

If [_KillTimedOutProcess_](./TPJCustomConsoleApp-KillTimedOutProcess.md) is _True_ the console application will be forcibly killed, otherwise the connection with the console application is simply broken and the application is left running.

The method has no effect when [_TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) is _INFINITE_.

## Remarks

The Windows API [_TerminateProcess_](http://msdn.microsoft.com/en-us/library/ms686714.aspx) function is used to forcibly kill child processes. This function does not perform a clean shut-down of the application. See Windows API documentation for details.
