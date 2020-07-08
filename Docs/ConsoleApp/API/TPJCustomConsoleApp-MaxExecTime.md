# MaxExecTime property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property MaxExecTime: LongWord;
```

## Description

This property specifies the maximum permitted execution time of a console application, in milliseconds. If the application runs for longer than _MaxExecTime_ then the [_Execute_](./TPJCustomConsoleApp-Execute.md) method returns once the time has elapsed. If the [_KillTimedOutProcess_](./TPJCustomConsoleApp-KillTimedOutProcess.md) property is _True_ then the console application is forcibly terminated, otherwise the process continues but no longer has any connection with this class.

_MaxExecTime_ may be set to _INFINITE_, in which case the console application will never time out and will always run to completion. In cases where the application is deemed to be running too long it may still be possible to force the application to terminate using the [_Terminate_](./TPJCustomConsoleApp-Terminate.md) method (but see remarks below).

The default property value is the value of the [_cDefMaxExecTime_](./Constants.md#cdefmaxexectime) constant.

## Remarks

You are strongly advised never to set both the _MaxExecTime_ and [_TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) properties to _INFINITE_. Doing so means that you can't kill an errant process by calling the [_Terminate_](./TPJCustomConsoleApp-Terminate.md) method. This may result in the parent application locking up.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
