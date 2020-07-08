# ProcessInfo property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property ProcessInfo: TProcessInformation;
```

## Description

_ProcessInfo_ is a read only property that provides process information for the executing console application. All fields are zero when no application is executing.

The property is only of use inside [_OnStart_](./TPJCustomConsoleApp-OnStart.md), [_OnWork_](./TPJCustomConsoleApp-OnWork.md) and [_OnComplete_](./TPJCustomConsoleApp-OnComplete.md) event handlers since these are the only way of accessing it when a process is running. Outside these events _ProcessInfo_ is undefined and should not be read.

## Remarks

See the Windows API documentation for information about the fields of _TProcessInformation_.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
