# DoComplete method

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
procedure DoComplete; virtual;
```

## Description

This virtual protected method triggers the [_OnComplete_](./TPJCustomConsoleApp-OnComplete.md) event. Descendants can override to perform specific actions without triggering the event. If the event is still required **inherited** can be called from within the overridden method.

The method would usually be implemented to perform any required actions to tidy up when a console application completes its run.
