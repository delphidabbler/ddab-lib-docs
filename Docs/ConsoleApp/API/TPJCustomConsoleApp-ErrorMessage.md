# ErrorMessage property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property ErrorMessage: string;
```

## Description

This read only property stores the error message corresponding the value of [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md), or the empty string if [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) is `0`.

If [_ErrorCode_](./TPJCustomConsoleApp-ErrorCode.md) corresponds to a Windows error then _ErrorMessage_ stores the error description provided by Windows.

## Remarks

The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
