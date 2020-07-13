# TimeToLive property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property TimeToLive: LongWord;
```

## Description

This read only property indicates the amount of time, in milliseconds, a console application has left to run before it times out.

The property is initialised to the value of the [_MaxExecTime_](./TPJCustomConsoleApp-MaxExecTime.md) property when the application starts and is decremented at the end of each time slice. When the application has completed the value is set to `0`.

## Remarks

It is only meaningful to examine the value of _TimeToLive_ in the [_OnStart_](./TPJCustomConsoleApp-OnStart.md), [_OnWork_](./TPJCustomConsoleApp-OnWork.md) and [_OnComplete_](./TPJCustomConsoleApp-OnComplete.md) event handlers.

If [_MaxExecTime_](./TPJCustomConsoleApp-MaxExecTime.md) is _INFINITE_ then _TimeToLive_ will always be _INFINITE_ while the application is executing.

If [_TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) is _INFINITE_ then _TimeToLive_ will always have the same value as [_MaxExecTime_](TPJCustomConsoleApp-MaxExecTime.md) until the application completes.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
