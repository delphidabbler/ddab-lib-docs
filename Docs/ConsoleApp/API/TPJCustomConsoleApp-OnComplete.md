# OnComplete event

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property OnComplete: TNotifyEvent;
```

## Description

This event is triggered when an application completes or times out. It is ***always*** called and is also guaranteed to be called after the last [_OnWork_](./TPJCustomConsoleApp-OnWork.md) event.

Handle this event to tidy up after the console process is completed. [_ProcessInfo_](./TPJCustomConsoleApp-ProcessInfo.md) is available when this event is triggered. The [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) property can be used to check how the application terminated: it will be zero if the application executed successfully, did not timeout and was not terminated.

## Remarks

The event is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
