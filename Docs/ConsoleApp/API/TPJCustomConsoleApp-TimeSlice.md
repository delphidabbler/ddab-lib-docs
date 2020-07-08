# TimeSlice property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property TimeSlice: LongWord;
```

## Description

Execution of a console application is normally time-sliced. This property determines the length of each time slice, in milliseconds. At the end of each time slice execution of the console application is paused, the length of time left to run is recalculated and the [_OnWork_](./TPJCustomConsoleApp-OnWork.md) event is triggered.

_TimeSlice_ may be set to _INFINITE_, in which case the console application is left to run until completion without interruption. In this case the [_OnWork_](./TPJCustomConsoleApp-OnWork.md) event will never be triggered and the application will never time out. Furthermore, it is not possible to force the application to terminate via the [_Terminate_](./TPJCustomConsoleApp-Terminate.md) method. Setting _TimeSlice_ to _INFINITE_ is not recommended.

The default property value is the value of the [_cDefTimeSlice_](./Constants.md#cdeftimeslice) constant.

## Remarks

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
