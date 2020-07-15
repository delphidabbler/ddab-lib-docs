# StdIn property

***Project:*** [Console Application Runner Classes](../API.md)

***Unit:*** [_PJConsoleApp_](./PJConsoleApp.md)

***Classes:*** [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md), [_TPJConsoleApp_](./TPJConsoleApp.md)

```pascal
property StdIn: THandle;
```

## Description

This property is used to optionally redirect a console application's standard input.

If _StdIn_ is set to `0` no redirection takes place.

Setting the property to a valid [inheritable handles](../InheritableHandles.md)  causes all input that the console application reads from standard input to actually be read from the specified handle.

The default property value is `0`.

## Remarks

When redirecting, the input handle can be attached to any object that is open for reading. Normally this will be a file or a pipe.

> The [I/O Utility Classes](../../IOUtils/API.md) library project has classes that are designed to help with opening pipes and files with [inheritable handles](../InheritableHandles.md).
>
The property is public in [_TPJConsoleApp_](./TPJConsoleApp.md) and protected in [_TPJCustomConsoleApp_](./TPJCustomConsoleApp.md).
