# OnStart event

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property OnStart: TNotifyEvent;
```

## Description

This event is triggered after console application process is created, just before it starts executing. It is ***always*** called before the first [_OnWork_](./TPJCustomConsoleApp-OnWork.md) event.

Handle this event to take any necessary action before the application starts executing. [_ProcessInfo_](./TPJCustomConsoleApp-ProcessInfo.md) is available when this event is triggered, so you will typically handle the event if you need access to process information at this stage.

## Remarks

The event is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
