# KillTimedOutProcess property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property KillTimedOutProcess: Boolean;
```

## Description

This property determines what happens when a console application times out or is terminated via a call to the [_Terminate_](./TPJCustomConsoleApp-Terminate.md) method.

When _KillTimedOutProcess_ is _True_ the console application is forcibly killed.

When the property is _False_ the application is left running but the [_Execute_](./TPJCustomConsoleApp-Execute.md) method returns and the link with the application is severed.

The default property value is _True_.

## Remarks

The Windows API [_TerminateProcess_](http://msdn.microsoft.com/en-us/library/ms686714.aspx) function is used to forcibly kill child processes. This function does not perform a clean shut-down of the application. See Windows API documentation for details.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
