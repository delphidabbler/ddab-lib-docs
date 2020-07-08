# ElapsedTime property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property ElapsedTime: LongWord;
```

## Description

This read only property gives the approximate time in milliseconds since the console application began executing. The clock stops when the application completes or times out.

This property is updated only when the application yields control to this class. The frequency with which this happens depends on the [_TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) property. If [_TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) is _INFINITE_ then _ElapsedTime_ is only updated once the application terminates.

Examine _ElapsedTime_ in an [_OnWork_](./TPJCustomConsoleApp-OnWork.md) event handler to get the updated execution time while a process is executing. Examine the property after a process has completed to get the total execution time.

Times are approximate.

## Remarks

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
