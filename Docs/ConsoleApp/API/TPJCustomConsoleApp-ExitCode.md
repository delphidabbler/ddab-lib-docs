# ExitCode property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property ExitCode: LongWord;
```

## Description

_ExitCode_ is a read only property that stores the exit code returned by the console application on completion. The value of the property is application dependent.

The value of _ExitCode_ is meaningless if the [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) property is non-zero.

## Remarks

Do not confuse _ExitCode_ with [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) which provides information about any problems encountered in actually running the application.

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
