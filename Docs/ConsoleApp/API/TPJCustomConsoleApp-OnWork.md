# OnWork event

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property OnWork: TNotifyEvent;
```

## Description

This event is triggered when the executing application yields control to this class. The frequency with which the event is triggered depends on the value of the [_TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) property - the smaller the value the more frequently the event is triggered.

Handle the event to perform any required processing between time slices. Examples of the kind of processing you may wish to perform are:

* Updating a progress meter in the main application, or reporting time to live or elapsed time since the application began executing.
* Processing data written by the console application to redirected standard output or standard error. The most common way to do this is via a pipe.
* GUI applications that update the user interface should call _Application.ProcessMessages_ in the _OnWork_ event handler to let the application refresh the interface.

This event is never triggered if [_TimeSlice_](./TPJCustomConsoleApp-TimeSlice.md) is _INFINITE_.

## Remarks

The event is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
